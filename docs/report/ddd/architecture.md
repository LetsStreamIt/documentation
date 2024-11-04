---
sidebar_position: 5
---

# Architecture Design

After identifying the bounded contexts and the main components of the system, we can now define the architecture of the system. The architecture will define how the components interact with each other and how the system will be deployed.

## Architecture Overview

We chose a **microservices architecture** for our system. This architecture style is well-suited for our system because it allows us to develop and deploy each component independently. This will make it easier to scale the system and add new features in the future. This architecture also allows us to use different technologies for each component, which can be beneficial for performance and scalability.

The system will be divided into the following components based on the bounded contexts identified in the analysis phase:

- **Frontend service**: This component will be responsible for serving the frontend application to the users. It will handle user interactions and display the content of the application.
- **Authentication service**: This component will be responsible for handling user authentication and authorization. It will provide endpoints for user registration, login, and logout.
- **Profile service**: This component will be responsible for managing user profiles. It will provide endpoints for viewing and editing user profiles.
- **Session service**: This component will be responsible for managing sessions. It will provide endpoints for creating, joining, and leaving sessions. It will also handle video playback synchronization and chat functionality.

The **frontend service** did not appear in the bounded contexts identified in the analysis phase. However, we decided to include it as a separate component because it will be responsible for serving the frontend application to the users. This will make it easier to scale the frontend independently from the backend services.

## Component and Connector View

This section describes the components and connectors of the system and how they interact with each other.

### Database per Microservice Service

Each microservice that requires a database will have its own database. This will allow each microservice to manage its own data independently. It will also make it easier to scale the system by scaling individual microservices.

![Database per Microservice](/img/ddd/architecture/db-microservice.svg)

## Interactions

Each microservice will expose a REST API that other microservices can use to interact with it. The frontend service will interact with the other microservices using their REST APIs. The microservices will interact with each other using REST APIs or message queues.

We decided against using an API gateway for this system because it adds unnecessary complexity.
Only having 3 microservices, it is not necessary to have an API gateway. We can directly call the microservices from the frontend service. Also an API gateway would introduce a single point of failure and a performance bottleneck, which would be undesirable for our system.

## Architecture

The following diagram shows the architecture of the system:

![Architecture](/img/ddd/architecture/architecture.svg)

## Deployment View

The system will be deployed using Docker containers. Orchestrating the containers will be done using Docker Compose. This will make it easier to deploy and scale the system.

The following diagram shows the deployment view of the system:

![Deployment](/img/ddd/architecture/deployment.svg)
