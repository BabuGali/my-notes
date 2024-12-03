**Resilience** is the ability of a software system **to recover from failures** and continue to function correctly. Resilience does not mean avoiding failures, but rather minimizing their impact and frequency. A resilient system can handle different types of failures, such as hardware faults, network outages, software bugs, or malicious attacks, and adapt to changing conditions and requirements.

**Fault tolerance** is the ability of a software system **to maintain its functionality and performance in the presence of faults**. Faults are any deviations from the expected or desired behavior of the system, such as errors, exceptions, or anomalies. A fault-tolerant system can detect, isolate, and correct faults, or at least tolerate them without compromising the system's integrity or availability.

Resilience and fault tolerance are important because they affect the reliability, availability, and security of your software systems. These are critical factors for user satisfaction, business continuity, and competitive advantage. If your system is not resilient or fault-tolerant, you risk losing data, functionality, performance, or trust, which can have serious consequences for your reputation, revenue, and reputation

**Resilience Methodologies:**
- Identifying failure points in architecture
- Load Balancing
- Health Check
- Cache

**Fault Tolerant Support the following policies** 
- Timeouts -
	- The Timeout policy prevents a request from waiting forever by setting a time limit on how long it can run. If the request exceeds the time limit, the timeout policy fails the request, even if it returns successfully. This policy saves an application from allocating resources to an unresponsive service.
- Retries 
	- In some cases, the underlying causes of an error or delay are momentary. The Retry policy saves an operation from failing on a momentary error by trying the operation again and giving it another chance to succeed.
- Fall-backs
	- The `@Fallback` annotation can be used as a last line of defense when other policies fail to solve an issue. The fallback starts after any other fault tolerance processing is complete. For example, if you use the `@Fallback` annotation together with the `@Retry` annotation, the fallback is called only after the maximum number of retries is exceeded.
- Circuit Breakers
	- The circuit breaker policy prevents repeated failures by setting conditions under which an operation fails immediately. If these conditions are met, the circuit breaker opens and fails the operation, which prevents repeated calls that are likely to fail.
	- here are three possible circuit states that are set by the circuit breaker. The transition between these states is determined by how the failure condition parameters are configured on the `@CircuitBreaker` annotation.

	- Closed: Under normal conditions, the circuit breaker is closed, which allows operations to continue running.
    
	- Open: When the configured error conditions are met, the circuit breaker opens and calls to the service that is operating under the circuit breaker fail immediately.
    
	- Half-open: After the configured delay period, an open circuit moves to a half-open state. In this state, the circuit accepts a configured number of trial calls. If any of these calls fail, the circuit breaker returns to the open state. If the configured number of trial calls succeed, the circuit moves to the closed state, which resumes normal operations.
- Bulkheads
- Asynchronus
- 