# Annotations

## _**@Insert, @Select, @Update, @Delete**_

Those annotations represent SQL statements to be executed by calling annotated methods:

```java
@Insert("Insert into person(name) values (#{name})")
public Integer save(Person person); 

@Update("Update Person set name= #{name} where personId=#{personId}")
public void updatePerson(Person person); 

@Delete("Delete from Person where personId=#{personId}")
public void deletePersonById(Integer personId); 

@Select("SELECT person.personId, person.name" + 
        "FROM person WHERE person.personId = #{personId}")
public Person getPerson(Integer personId);
```

## _**@Results**_ 

It is a list of result mappings that contain the details of how the database columns are mapped to Java class attributes:

```java
@Select("Select personId, name from Person where personId=#{personId}")
@Results(value = {  
    @Result(property = "personId", column = "personId")    
    // ...   
})
public Person getPersonById(Integer personId);
```

### _**@Result**_ 

It represents a single instance of _Result_ out of the list of results retrieved from _@Results._ It includes the details like mapping from database column to Java bean property, Java type of the property and also the association with other Java objects:

```java
@Results(value = {  
    @Result(property = "personId", column = "personId"),  
    @Result(property="name", column = "name"),  
    @Result(property = "addresses", javaType =List.class)     
    // ... 
})
public Person getPersonById(Integer personId);
```

### _**@Many**_ 

It specifies a mapping of one object to a collection of the other objects:

```java
@Results(value ={  
    @Result(property = "addresses", javaType = List.class, 
            column = "personId", many=@Many(select = "getAddresses"))
    })
```

Here _getAddresses_ is the method which returns the collection of _Address_ by querying Address table.

```java
@Select("select addressId, streetAddress, personId" + 
        "from address where personId=#{personId}")
public Address getAddresses(Integer personId);
```

Similar to _@Many_ annotation, we have _@One_ annotation which specifies the one to one mapping relationship between objects.

### _**@MapKey**_ 

This is used to convert the list of records to _Map_ of records with the key as defined by _value_ attribute:

```java
@Select("select * from Person")
@MapKey("personId")
public Map<Integer, Person> getAllPerson();
```

### _**@Options**_

This annotation specifies a wide range of switches and configuration to be defined so that instead of defining them on other statements we can _@Options_ to define them:

```java
@Insert("Insert into address (streetAddress, personId)" +
   "values(#{streetAddress}, #{personId})")
@Options(useGeneratedKeys = false, flushCache=true)
public Integer saveAddress(Address address);
```

