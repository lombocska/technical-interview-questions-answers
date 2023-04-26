# EXPECTED KNOWLEDGE FROM A MEDIOR BACKEND DEVELOPER


<p align="center">
  <a href="#distributed-systems">Distributed systems</a> •
  <a href="#asynchronous-messaging">Asynchronous messaging</a> •
  <a href="#ddd">DDD</a> •
  <a href="#spring-ecosystem">Spring ecosystem</a> •
  <a href="#functional-programming">Functional Programming</a>
  <a href="#akka-framework">Akka framework</a>
  <a href="#docker">Docker</a>
</p>

## Distributed systems

A distributed system is a collection of independent components located on different machines that share messages with each other in order to achieve common goals.
The hope is that together, the system can maximize resources and information while preventing failures, as if one system fails, it won't affect the availability of the service.

The most important functions of distributed computing are:

- Resource sharing - whether it’s the hardware, software or data that can be shared
- Openness - how open is the software designed to be developed and shared with each other
- Concurrency - multiple machines can process the same function at the same time
- Scalability - how do the computing and processing capabilities multiply when extended to many machines
- Fault tolerance - how easy and quickly can failures in parts of the system be detected and recovered
- Transparency - how much access does one node have to locate and communicate with other nodes in the system.

A homogenous distributed database means that each system has the same database management system and data model. They are easier to manage and scale performance by adding new nodes and locations.
Heterogenous distributed databases allow for multiple data models, different database management systems. Gateways are used to translate the data between nodes and usually happen as a result of merging applications and systems.

### Some Patterns of distributed systems

**Idempotent Receiver**

Identify requests from clients uniquely so they can ignore duplicate requests when client retries
Solution: Identify a client uniquely by assigning a unique id to each client. Before sending any requests, the client registers itself with the server.

**Two Phase Commit**
Update resources on multiple nodes in one atomic operation.
Solution: The essence of two phase commit, unsurprisingly, is that it carries out an update in two phases:

- the first, prepare, asks each node if it's able to promise to carry out the update
- the second, commit, actually carries it out.

**Leader and Followers**
Have a single server to coordinate replication across a set of servers.
Solution: Select one server amongst the cluster as leader. The leader is responsible for taking decisions on behalf of the entire cluster and propagating the decisions to all the other servers.


### Advantages of Distributed Systems

The ultimate goal of a distributed system is to enable the scalability, performance and high availability of applications.

- Unlimited Horizontal Scaling - machines can be added whenever required.
- Low Latency - having machines that are geographically located closer to users, it will reduce the time it takes to serve users.
- Fault Tolerance - if one server or data centre goes down, others could still serve the users of the service.


### Disadvantages of Distributed Systems

Every engineering decision has trade offs. Complexity is the biggest disadvantage of distributed systems. There are more machines, more messages, more data being passed between more parties which leads to issues with:

- Data Integration & Consistency
being able to synchronize the order of changes to data and states of the application in a distributed system is challenging, especially when there nodes are starting, stopping or failing.

- Network and Communication Failure
messages may not be delivered to the right nodes or in the incorrect order which lead to a breakdown in communication and functionality.

- Management Overhead
more intelligence, monitoring, logging, load balancing functions need to be added for visibility into the operation and failures of the distributed systems


## Asynchronous messaging

Asynchronous Messaging is a communication method where participants on both sides of the conversation have the freedom to start, pause, and resume conversational messaging on their own terms, eliminating the need to wait for a direct live connection (aka synchronous messages).
People often send a message asynchronously when they do not require an immediate response from the recipient. Today, messaging is a communication channel most customers prefer to use not just with friends and family, but also with brands.


## DDD

> Domain-Driven Design is an approach to software development that centers the development on programming a domain model that has a rich understanding of the processes and rules of a domain."
> The idea that software systems need to be based on a well-developed model of a domain has been around.
> .... the idea that to develop software for a complex domain, we need to build Ubiquitous Language that embeds domain terminology into the software systems that we build.

https://martinfowler.com/bliki/DomainDrivenDesign.html

keywords for this topic: extreme programming, bounded contexts, ubiquitous language

*Extreme Programming (XP)* : software development methodology
*Bounded Contexts*: a central pattern in Domain-Driven Design. It is the focus of DDD's strategic design section which is all about dealing with large models and teams. DDD deals with large models by dividing them into different Bounded Contexts and being explicit about their interrelationships.
DDD divides up a large system into Bounded Contexts, each of which can have a unified model - essentially a way of structuring MultipleCanonicalModels.
*Ubiquitous Language*: the term Eric Evans uses in Domain Driven Design for the practice of building up a common, rigorous language between developers and users.

## Spring ecosystem

https://spring.io/projects

## Functional Programming

Functional programming (FP) is an approach to software development that uses pure functions to create maintainable software. In other words, building programs by applying and composing functions.

Functional programming harnesses language support by using functions as variables, arguments, and return values—creating elegant and clean code in the process. FP also uses immutable data and avoids concepts like shared states. This is in contrast to object-oriented programming (OOP), which uses mutable data and shared states.

Functional programming languages focus on declarations and expressions rather than the execution of statements. Functions are also treated like first-class citizens—meaning they can pass as arguments, return from other functions, and attach to names.

FP focuses on the results, not the process, while iterations like loop statements and conditional statements (e.g., If-Else) aren’t supported.


## Docker

Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. By taking advantage of Docker’s methodologies for shipping, testing, and deploying code quickly, you can significantly reduce the delay between writing code and running it in production.
Docker provides the ability to package and run an application in a loosely isolated environment called a container. The isolation and security allows you to run many containers simultaneously on a given host. Containers are lightweight and contain everything needed to run the application, so you do not need to rely on what is currently installed on the host. You can easily share containers while you work, and be sure that everyone you share with gets the same container that works in the same way.
The underlying technology🔗
Docker is written in the Go programming language and takes advantage of several features of the Linux kernel to deliver its functionality. Docker uses a technology called namespaces to provide the isolated workspace called the container. When you run a container, Docker creates a set of namespaces for that container.

https://docs.docker.com/get-started/overview/


## Kafka

Kubernetes or Kafka Control Plane
Products like Kubernetes or Kafka's architecture are built around a strongly consistent metadata store. We can understand it as a pattern sequence. Consistent Core is used as a strongly consistent, fault tolerant metadata store. Lease is used to implement group membership and failure detection of cluster nodes. Cluster nodes use State Watch to get notified when any cluster node fails or updates its metadata The Consistent Core implementation uses Idempotent Receiver to ignore duplicate requests sent by cluster nodes in case of retries on network failure. The Consistent Core is built with a 'Replicated Wal', which is described as a pattern sequence in the above section.
The Consistent Core implementation uses Idempotent Receiver to ignore duplicate requests sent by cluster nodes in case of retries on network failure. The Consistent Core is built with a 'Replicated Wal', which is described as a pattern sequence in the above section.