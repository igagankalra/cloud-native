# Architecture Consideration for Cloud Native

## Design Considerations for Cloud-Native Applications
The first step in the context discovery process is to list the __functional requrements__, or what application capabilities should be delivered to the end-users. For example, a good starting point is to expand on the following:
- Stakeholders
- Fuctionalities
- End users
- Input and output process
- Engineering teams

The second step is to enumarate the __available resources__ that faicilitates the implementation of the project, For example, a good starting point is to list avalable:
- Engineering resources
- Financial resources
- Timeframes
- Internal knowledge

Having a good understanding of fuctional requirements and available resources can lead to a simpler choice between monolithic and microservice-based architectures.

## Monoliths and Microservices
Each architecture encapsulates the 3 main tires of an application:
- UI (User Interface) - handles HTTP requests from the users and returns a response
- Business logic - containes the code that provides a service to the user
- Data layer - implements access and storage of data objects

In a monolithic architecture, application tiers can be described as:
- part of the same unit
- managed in a single repository
- sharing existing resources (e.g. CPU and mmemory)
- developed in one programming language
- released using a single binary

In a miroservice architecture, application tiers are managed idependently, as different units. Each unit has the following characteristics:
- managed in a separate repository
- own allocated resources (e.g. CPU and memory)
- well-defined API (Application Programming Interface) for connection to other units
- implemented using the programming language of choice
- released using its own binary

## Trade-offs for Monoliths and Microservices
Choosing between Monoloths and Microservices is a trade-off in development complexity, scalability, time to deploy, flexibility, operational cost, and reliability.

__Development complexity__ refers to the efford required to deploy and manage an application
- _Monoliths_ - one poragramming language; one repository; enables sequential development
- _Microservice_ - multiple programming languages; multiple repositories; enables concurrent development

__Scalability__ refers to how an application is able to scale up and down, based on the incoming traffic.
- _Monoliths_ - replication of the entire stack; hence it's heavy on resource consumption
- _Microservice_ - replication of a single unit, providing on demand consumption of resources

__Time to Deploy__ encapsulates the build of a delivery pipeline that is used to ship features.
- _Monoliths_ - one delivery pipeline that deploys the entire stack; more risk with each development leading to a lower velocity rate.
- _Microservice_ - multiple delivery pipelines that deploy separate units; less risk with each deployment leading to a higher feature development rate.

__Flexibility__ implies the ability to adopt to new technologies and introduce new functionalities.
- _Monoliths_ - low rate, since the entire application stack might need restructuring to incorporate new functionalities
- _Microservice_ - high rate, since changing an independent unit is straightforward.

__Operational Cost__ represents the cost of necessary resources to release a product.
- _Monoliths_ - low initial cost, since one code base and one pipeline should be managed. However, the cost increases rapidly when the application needs to operate at scale.
- _Microservice_ - high initial cost, since multiple repositories and pipelines require managment. However, at scale, the cost remains proportional to the consumed resources.

__Reliability__ refers to how resilient an application is and it's ability to recover from failure.
- _Monoliths_ - In a failure scenario, the entire stack needs to be recovered. Also, the visibility into each functionality is low, since all the logs and metrics are aggregated together.
- _Microservices_ in a failure scenario, only the failed unit needs to be recovered. Also, there is high visibility into the logs and metrics for each unit.

## Best Practices for Application Deployment
__Health checks__ are implemented to showcase the status of an application. These checks report if an application is running and meets the expected behavior to serve incomming traffic. Usually health checks are represented by an HTTP endpoint such as `/healthz` or `/status`. These endpoints return an HTTP response showcasing if the application is healthy or in an error state.

__Metrics__ are necessary to quantify the performace of the application. To fully understand how a service handles requests, it is mandatory to collect statistics on how the service operates. For example, the number of active users, handled requests, or the number of logins. Additionally, it is paramount to gather statistics on resources that the application requires to be fully operational. For example, the amount of CPU, memory, and network throughput. Usually, the collection of metrics are returned via an HTTP endpoint such as `/metrics`, which contains the internal metrics such as the number of active users, consumed CPU, network throughput, etc.

__Logs__ aggregation provides valuable insights into what operations a service is performing at a point in time. It is the nucleus of any troubleshooting and debugging process. For example, it is essential to record if a user logged in successfully into a service, or encountered an error while performing a payment.

There are multiple logging levels that can be attributed to an operation. Some of the most widely used are:
- DEBUG - record fine-grained events of application processes
- INFO - provide coarse-grainded information about an operation
- WARN - records a potentioal issue with the service
- ERROR - notifies an error has been encountered. however, the application is still running.
- FATAL - represents a critical situation, when the application is not operational.

As well, it is common practice to associate each log line with a __timestamp__, that will exactly record when an operation was invoked.

__Tracing__ is capable of creating a full picture of how different services are invoked to fullfill a single request. Usually, racing is integrated through a library at the application layer, where the developer can record when a particular service is invoked. These records for individual services are defined as spans. A collection of spans define a trace that recreates the entire lifecycle of a request.

__Resource consumption__ encapsulates the resource an application requires to be fully operational. This usually refers to the amount of CPU and memory that is consumed by an application during it's execution. Additionally, it is beneficial to benchmark the network throughput, or how many requests can an application handle concurrently. Having awareness of the resource boundaries is essential to ensure that the application is up and running 24/7.
