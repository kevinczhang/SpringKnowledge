---
description: >-
  Coherence can perform queries and indexes against currently cached data that
  meets a given set of criteria.
---

# Querying

Queries and indexes can be simple, employing filters packaged with Coherence, or they can be run against multi-value attributes such as collections and arrays.

 It should be noted that queries apply only to currently cached data \(and do not use the `CacheLoader` interface to retrieve additional data that may satisfy the query\). Thus, the data set should be loaded entirely into cache before queries are performed.

## Query filters

 The concept of querying is based on the [`ValueExtractor`](https://docs.oracle.com/cd/E24290_01/coh.371/e22843/toc.htm) interface.  Most developers need only the [`ReflectionExtractor`](https://docs.oracle.com/cd/E24290_01/coh.371/e22843/toc.htm) implementation of this interface. The implementation uses reflection to extract an attribute from a value object by referring to a method name which is typically a getter method.

```java
ValueExtractor extractor = new ReflectionExtractor("getName");
```

 Any `void` argument method can be used, including `Object` methods like `toString().`

A filter has a single method which determines whether a given object meets a criterion.

```java
Filter filter = new EqualsFilter(extractor, "Bob Smith");
Filter filter = new EqualsFilter("getName", "Bob Smith");
for (Iterator iter = cache.entrySet(filter).iterator(); iter.hasNext(); )
{
    Map.Entry entry = (Map.Entry)iter.next();
    Integer key = (Integer)entry.getKey();
    Person person = (Person)entry.getValue();
    System.out.println("key=" + key + " person=" + person);
}
```

## Using Query Indexes

### Creating an Index

 The `addIndex` method of the [`QueryMap`](https://docs.oracle.com/cd/E24290_01/coh.371/e22843/toc.htm) class is used to create indexes. Any attribute able to be queried may be indexed using this method. The method includes three parameters:

```java
addIndex(ValueExtractor extractor, boolean fOrdered, Comparator comparator)
```

```java
NamedCache cache = CacheFactory.getCache("MyCache");
ValueExtractor extractor = new ReflectionExtractor("getAttribute");
cache.addIndex(extractor, true, null);
```

 The `fOrdered` argument specifies whether the index structure is sorted. Sorted indexes are useful for range queries, such as "select all entries that fall between two dates" or "select all employees whose family name begins with 'S'". For "equality" queries, an unordered index may be used, which may have better efficiency in terms of space and time.

#### Creating User-Defined Indexes

**Implementing the MapIndex Interface**

```java
public class CustomMapIndex implements MapIndex
   {
   public void insert(Map.Entry entry)
       {
       if (entry.getValue()!= null)
           {
           ...
           }
       }
   ...
   }
```

 **Implementing the IndexAwareExtractor Interface**

 The `IndexAwareExtractor` interface is an extension to the `ValueExtractor` interface that supports the creation and destruction of a `MapIndex` index. Instances of this interface are intended to be used with the `QueryMap` API to support the creation of custom indexes. 

```java
public class CustomIndexAwareExtractor
        implements IndexAwareExtractor, ExternalizableLite, PortableObject
    {
    public CustomIndexAwareExtractor(ValueExtractor extractor)
        {
        m_extractor = extractor;
        }
 
    public MapIndex createIndex(boolean fOrdered, Comparator comparator,
            Map mapIndex)
        {
        ValueExtractor extractor = m_extractor;
        MapIndex       index     = (MapIndex) mapIndex.get(extractor);
 
        if (index != null)
            {
            throw new IllegalArgumentException(
                    "Repetitive addIndex call for " + this);
            }
 
        index = new CustomMapIndex(extractor, fOrdered, comparator);
        mapIndex.put(extractor, index);
        return index;
        }
 
    public MapIndex destroyIndex(Map mapIndex)
        {
        return (MapIndex) mapIndex.remove(m_extractor);
        }
    ...
    }
```

### **Using a Conditional Index**

 A conditional index is a custom index that implements both the `MapIndex` and `IndexAwareExtractor` interfaces as described above and uses an associated filter to evaluate whether an entry should be indexed. 

```java
ValueExtractor extractor = new ReflectionExtractor("getLastName");
Filter filter = new NotEqualsFilter("getId", null);
ValueExtractor condExtractor = new ConditionalExtractor(filter, extractor, true);
 
// add the conditional index which should only contain the last name values for the
// entries with non-null Ids
cache.addIndex(condExtractor, true, null);
```

## Performing Batch Queries

 Using the `key set` form of the queries – combined with `getAll()` – reduces memory consumption since the entire entry set is not deserialized on the client simultaneously. It also takes advantage of near caching.

```java
// key set(Filter filter)
Set setKeys = cache.key set(filter);
Set setPageKeys = new HashSet();
int PAGE_SIZE = 100;
for (Iterator iter = setKeys.iterator(); iter.hasNext();)
    {
    setPageKeys.add(iter.next());
    if (setKeyPage.size() == PAGE_SIZE || !iter.hasNext())
        {
        // get a block of values
        Map mapResult = cache.getAll(setPageKeys);

        // process the block
        // ...

        setPageKeys.clear();
        }
    }
```

## Performing Queries on Multi-Value Attributes

 Coherence supports indexing and querying of multi-value attributes including collections and arrays. When an object is indexed, Coherence verifies if it is a multi-value type, and then indexes it as a collection rather than a singleton. The [`ContainsAllFilter`](https://docs.oracle.com/cd/E24290_01/coh.371/e22843/toc.htm), [`ContainsAnyFilter`](https://docs.oracle.com/cd/E24290_01/coh.371/e22843/toc.htm) and [`ContainsFilter`](https://docs.oracle.com/cd/E24290_01/coh.371/e22843/toc.htm) are used to query against these collections.

```java
Set searchTerms = new HashSet();
searchTerms.add("java");
searchTerms.add("clustering");
searchTerms.add("books");

// The cache contains instances of a class "Document" which has a method
// "getWords" which returns a Collection<String> containing the set of
// words that appear in the document.
Filter filter = new ContainsAllFilter("getWords", searchTerms);

Set entrySet = cache.entrySet(filter);

// iterate through the search results
// ...
```



