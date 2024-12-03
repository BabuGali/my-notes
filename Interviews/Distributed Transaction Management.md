	- TWO PAHSE Commit
	- Saga Pattern
# Two Phase Commit
- We introduce a new entity called `Transaction Coordinator` . This entity orchestrates the commit part of the transaction. Other servers managing the individual transactions are known as `Participants`.
- ![[Two Phase Commit.png]]
- **Drawbacks of Two Phase commit**
	- Latency
	- Transaction Coordinator - single point of failure
	- Participants dependency  - A slow participant affects the performance of other participants. Total transaction time is proportional to the time taken by the slowest server.
# Sega Pattern
- The **saga** design pattern is provide to manage data consistency across microservices in **distributed transaction** cases.
- In the context of distributed transactions, the SAGA pattern can help ensure that the overall transaction is either completed successfully, or is rolled back to its initial state if any individual microservice encounters an error.
- Basically, saga patterns offers to create a **set** of **transactions** that **update microservices sequentially**,  and publish events to trigger the next transaction for the next microservices.If one of the step is failed, than **saga patterns** trigger to **rollback transactions** which is basically do reverse operations with **publishing rollback** events to previous microservices.
- Two ways we can implement Saga Pattern
	- Choreography Saga Pattern
	- Orchestration Saga Pattern
### Choreography Saga Pattern
- Choreography provides to coordinate sagas with applying publish-subscribe principles. With choreography, each microservices run its own local transaction and publishes events to **message broker system** and that trigger **local transactions** in other microservices.
- But if **Saga Workflow** steps increase, then it can become confusing and hard to manage transaction between saga microservices.
- ![[Choreography Saga Pattern.png]]
### Orchestration Saga Pattern
- The orchestrator microservices execute **saga transaction** and manage them in centralized way and if one of the step is failed, then executes rollback steps with compensating transactions.
- Orchestration way is good for complex workflows which includes lots of steps. But this makes **single point-of-failure** with centralized controller microservices and need implementation of complex steps.
#### Rollback of Saga Pattern
- To use the SAGA pattern in a distributed transaction, we can use a **compensating transaction** to undo the changes made by each microservice in the event of an error.
# When to use SAGA and 2 PC commit in Design?
- 2 Phase commit typically used in _scenarios with a small number of participants,_ where the latency and scalability limitations of 2PC can be managed.
- In contrast, SAGA pattern is useful in situations where the transaction is too large to be managed by a single 2PC protocol**. SAGA breaks the transaction down into smaller, local transactions that can be independently managed by each microservice.
- In summary, 2PC is a distributed protocol that coordinates transaction commits, while the Saga pattern is a design pattern for managing long-lived transactions by breaking them down into a sequence of local transactions that can be compensated for if necessary.
