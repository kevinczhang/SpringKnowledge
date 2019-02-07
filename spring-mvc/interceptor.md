# Interceptor

Spring **HandlerInterceptor** declares three methods based on where we want to intercept the HTTP request.

1. **boolean preHandle\(HttpServletRequest request, HttpServletResponse response, Object handler\)**: This method is used to intercept the request before it’s handed over to the handler method. This method should return ‘true’ to let Spring know to process the request through another spring interceptor or to send it to handler method if there are no further spring interceptors.

   If this method returns ‘false’ [Spring framework](https://www.journaldev.com/16922/spring-framework) assumes that request has been handled by the spring interceptor itself and no further processing is needed. We should use response object to send response to the client request in this case.

   Object _handler_ is the chosen handler object to handle the request. This method can throw Exception also, in that case [Spring MVC Exception Handling](https://www.journaldev.com/2651/spring-mvc-exception-handling-controlleradvice-exceptionhandler-handlerexceptionresolver) should be useful to send error page as response.

2. **void postHandle\(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView\)**: This HandlerInterceptor interceptor method is called when HandlerAdapter has invoked the handler but DispatcherServlet is yet to render the view. This method can be used to add additional attribute to the ModelAndView object to be used in the view pages. We can use this spring interceptor method to determine the time taken by handler method to process the client request.
3. **void afterCompletion\(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex\)**: This is a HandlerInterceptor callback method that is called once the handler is executed and view is rendered.

If there are multiple spring interceptors configured, _preHandle\(\)_ method is executed in the order of configuration whereas _postHandle\(\)_ and _afterCompletion\(\)_ methods are invoked in the reverse order.

```java
public class RequestProcessingTimeInterceptor extends HandlerInterceptorAdapter {

	private static final Logger logger = LoggerFactory
			.getLogger(RequestProcessingTimeInterceptor.class);

	@Override
	public boolean preHandle(HttpServletRequest request,
			HttpServletResponse response, Object handler) throws Exception {
		long startTime = System.currentTimeMillis();
		logger.info("Request URL::" + request.getRequestURL().toString()
				+ ":: Start Time=" + System.currentTimeMillis());
		request.setAttribute("startTime", startTime);
		//if returned false, we need to make sure 'response' is sent
		return true;
	}

	@Override
	public void postHandle(HttpServletRequest request,
			HttpServletResponse response, Object handler,
			ModelAndView modelAndView) throws Exception {
		System.out.println("Request URL::" + request.getRequestURL().toString()
				+ " Sent to Handler :: Current Time=" + System.currentTimeMillis());
		//we can add attributes in the modelAndView and use that in the view page
	}

	@Override
	public void afterCompletion(HttpServletRequest request,
			HttpServletResponse response, Object handler, Exception ex)
			throws Exception {
		long startTime = (Long) request.getAttribute("startTime");
		logger.info("Request URL::" + request.getRequestURL().toString()
				+ ":: End Time=" + System.currentTimeMillis());
		logger.info("Request URL::" + request.getRequestURL().toString()
				+ ":: Time Taken=" + (System.currentTimeMillis() - startTime));
	}

}
```

