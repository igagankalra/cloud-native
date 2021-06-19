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
