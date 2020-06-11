# Hystrix

 Netflix has created a library called **Hystrix**. It implements the circuit breakers pattern. Circuit breakers calculate when to open and close the circuit and what to do in case of failure. When all services fail at some point, the circuit breaker handles these failures gracefully. The circuit breakers have three states: **OPEN, CLOSED,** and **HALF-OPEN** State.

![](../../../.gitbook/assets/image%20%283%29.png)

 **CLOSED State:** If the Circuit breaker is in the CLOSED state and all calls pass through to the supplier microservices. It responds without any latency.

 **OPEN State:** The circuit breaker returns an error calls without executing the function.

**HALF-OPEN State:** The circuit turns to HALF-OPEN state when a function execution is **timed out**. It test that underlying problem still exists or not. It is a **monitoring** and **feedback mechanism**. It makes a trial call to supplier microservices to check if it has recovered. If the call to the supplier is timed out, then the circuit remains in the **OPEN** state. If the call return success, the circuit-switched to the **CLOSED** state. The circuit breaker returns all external calls to the service with an error during the **HALF-OPEN** State.

