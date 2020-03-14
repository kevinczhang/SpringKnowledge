# Spring MVC

Spring MVC is based on Model-View-Controller architecture.

![Spring MVC architecture ](../../../.gitbook/assets/image%20%2811%29.png)

`DispatcherServlet` is the front controller class to take all requests and start processing them. We have to configure it in web.xml file. It’s job is to pass request to appropriate controller class and send the response back when view pages have rendered the response page.

## Exception Handling

**Controller Based** – We can define exception handler methods in our controller classes. All we need is to annotate these methods with `@ExceptionHandler` annotation. This annotation takes Exception class as argument. So if we have defined one of these for Exception class, then all the exceptions thrown by our request handler method will have handled.

**Global Exception Handler** – Exception Handling is a cross-cutting concern, it should be done for all the pointcuts in our application and that’s why Spring provides `@ControllerAdvice` annotation that we can use with any class to define our global exception handler.

**HandlerExceptionResolver** – For generic exceptions, most of the times we serve static pages. `SimpleMappingExceptionResolver` is the default implementation class, it allows us to configure exceptionMappings where we can specify which resource to use for a particular exception. We can also override it to create our own global handler with our application specific changes, such as logging of exception messages.

```java
@ControllerAdvice
public class GlobalExceptionHandler {

    private static final Logger logger = LoggerFactory.getLogger(GlobalExceptionHandler.class);

    @ExceptionHandler(SQLException.class)
    public String handleSQLException(HttpServletRequest request, Exception ex){
        logger.info("SQLException Occured:: URL="+request.getRequestURL());
        return "database_error";
    }

    @ResponseStatus(value=HttpStatus.NOT_FOUND, reason="IOException occured")
    @ExceptionHandler(IOException.class)
    public void handleIOException(){
        logger.error("IOException handler executed");
        //returning 404 error code
    }

    @ExceptionHandler(EmployeeNotFoundException.class)
    public @ResponseBody ExceptionJSONInfo handleEmployeeNotFoundException(HttpServletRequest request, Exception ex){

        ExceptionJSONInfo response = new ExceptionJSONInfo();
        response.setUrl(request.getRequestURL().toString());
        response.setMessage(ex.getMessage());

        return response;
    }
}
```

