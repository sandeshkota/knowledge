### how do you manage distributed transactions?
- Suppose we need to update the data of two microservices and also we need to ensure that either both should get updated OR none should get updated, which is also called as atomicity. In a database system, atomicity means that in a transaction either all steps complete or no steps complete. 
- There are two ways of solving this problem
	- 2pc (2 phase commit) : 2pc has two phases: A prepare phase and a commit phase. In the prepare phase, all microservices will be asked to prepare for some data change that could be done atomically (and also locks the object). Once all microservices are prepared, the commit phase will ask all the microservices to make the actual changes.
	- Saga : In a Saga pattern, the distributed transaction is fulfilled by asynchronous local transactions on all related microservices. The microservices communicate with each other through an event bus. (Event driven architecture with message broker)

![Saga failure](https://developers.redhat.com/sites/default/files/blog/2018/09/Untitled-UML-9.png)

In the example above, the OrderMicroservice receives a request to place an order. It first starts a local transaction to create an order and then emits an OrderCreated event. The CustomerMicroservice listens for this event and updates a customer fund once the event is received. If he UpdateCustomerFund failed for some reason and it then emitted a CustomerFundUpdateFailed event. The OrderMicroservice listens for the event and start its compensation transaction to revert the order that was created.

Disadvantage of the Saga pattern is it does not have read isolation. For example, the customer could see the order being created, but in the next second, the order is removed due to a compensation transaction.

