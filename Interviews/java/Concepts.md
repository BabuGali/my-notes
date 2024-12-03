# Serialization and Deserialization and Externalization
- Serialization is a mechanism of converting the state of an object into a byte stream.
- Deserialization is the reverse process where the byte stream is used to recreate the actual Java object in memory
- The byte stream created is platform independent.
- To make a Java object serializable we implement the ****java.io.Serializable**** interface
- The ObjectOutputStream class contains ****writeObject()**** method for serializing an Object.
-  If a parent class has implemented Serializable interface then child class doesn’t need to implement it but vice-versa is not true.
-  Only non-static data members are saved via Serialization process.
- Static data members and transient data members are not saved via Serialization process.
- Constructor of object is never called when an object is deserialized.
- ****final**** variables will be participated into serialization directly by their values.  Hence declaring a final variable as transient there is no use.
##Externalization
- **Externalization** in Java is used to customize the serialization mechanism. Java serialization is not much efficient. When we have bloated objects that hold several attributes and properties, it is not good to serialize them.
-  if we have implemented the Serialization interface in a class, we can externalize it using the **writeExternal()** method. When users reconstruct an externalized object from their end, an instance of the object will be created using the **readExternal()** method.
- implements **Externalizable**
- For the primitive type values, the writeBoolean(), writeByte(), writeInt(), writeLong() methods are used.
- For strings, arrays, and custom classes, the writeObject() method is used.
![[Serialization Vs Externalization.png]]

#### Overload and Override
- Method overloading is compile  time  and method overriding is at runtime
- Method overloading occurs with in the class, method overriding comes with inheritance
- private and final methods can be overloaded but cannot be overridden
- in overloading arguments should be differ, but in overriding should be same
- in overloading, return type can or cannot be the same. but in overriding return type must be same or **co-varient**
- it is possible to have different return types for an overriding method in the child class, but the child’s return type should be a subtype of the parent’s return type.
- 
#### Thread
- Different types of thread -user thread and daemon thread
- When all the user threads are executed, JVM terminates the program.
- **Thread priority** - When we create a thread, we can assign its priority. We can set different priorities to different Threads but it doesn’t guarantee that a higher priority thread will execute first than a lower priority thread. The thread scheduler is the part of Operating System implementation and when a Thread is started, its execution is controlled by Thread Scheduler and JVM doesn’t have any control over its execution.
- How to create thread-  by either implementing **Runnable** interface or by extending **Thread** Class.
- thread sleep
- thread join
- thread states
- wait, notify and notifyall
- thread safety and schronization
- Thread dump - **Java Thread dump** provides the information of the current thread. A thread dump is useful to analyze performance issues with the application. You can use thread dump to find and fix deadlock situations
- Thread life cycle 
- ![[thread life cycle.png]]
- thread pool
-  What is the difference between synchronous and asynchronous programming? - Synchronous programming is when you assign a single task to a single thread. Asynchronous programming is when multiple threads share a single task.'
- Thread scheduler
- Can you start a thread twice?
- deadlock situation
- livelock
- thread communication
- difference between wait and sleep
- threadlocal
- daemon thread
- thread saftey
- 
- 
