# Expression Language

 The **Expression Language** \(EL\) simplifies the accessibility of data stored in the Java Bean component, and other objects like request, session, application etc.

#### Implicit Objects in Expression Language

| Implicit Objects | Usage |
| :--- | :--- |
| pageScope | it maps the given attribute name with the value set in the page scope |
| requestScope | it maps the given attribute name with the value set in the request scope |
| sessionScope | it maps the given attribute name with the value set in the session scope |
| applicationScope | it maps the given attribute name with the value set in the application scope |
| param | it maps the request parameter to the single value |
| paramValues | it maps the request parameter to an array of values |
| header | it maps the request header name to the single value |
| headerValues | it maps the request header name to an array of values |
| cookie | it maps the given cookie name to the cookie value |
| initParam | it maps the initialization parameter |
| pageContext | it provides access to many objects request, session etc. |

### Examples

{% code title="index.jsp" %}
```markup
<form action="process.jsp">  
    Enter Name:<input type="text" name="name" /><br/><br/>  
    <input type="submit" value="go"/>  
</form>
```
{% endcode %}

{% code title="process.jsp" %}
```markup
Welcome, ${ param.name }  
```
{% endcode %}

## Precedence of Operators

There are many operators that have been provided in the Expression Language. Their precedence are as follows:

| \[\] . |
| :--- |
| \(\) |
| -\(unary\) not ! empty |
| \* / div % mod |
| + - \(binary\) |
| &lt; &lt;= &gt; &gt;= lt le gt ge |
| == != eq ne |
| && and |
| \|\| or |
| ?: |

## Reserve words in EL

There are many reserve words in the Expression Language. They are as follows:

| lt | le | gt | ge |
| :--- | :--- | :--- | :--- |
| eq | ne | true | false |
| and | or | not | instanceof |
| div | mod | empty | null |

