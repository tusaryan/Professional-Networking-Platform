# Professional Networking Platform Backend (Microservices)

## Overview
**(Will update this guide soon for detailed setup)**
This project is the backend implementation for a Professional Networking Platform, built using a microservices architecture with Spring Boot and Spring Cloud. It demonstrates various patterns common in distributed systems.

The system consists of the following core microservices:

* **`discovery-server`**: Handles service registration and discovery using Spring Cloud Netflix Eureka. Allows services to find each other dynamically.
* **`api-gateway`**: Single entry point for all client requests. Routes requests to appropriate downstream services, handles authentication (JWT), and potentially rate limiting/cross-cutting concerns. Uses Spring Cloud Gateway.
* **`user-service`**: Manages user registration, authentication, profiles, and JWT generation/validation.
* **`connections-service`**: Handles user connection requests, follow/unfollow logic, and maintains the social graph.
* **`posts-service`**: Manages creation, retrieval, liking, and potentially commenting on posts.
* **`notification-service`**: Generates and manages user notifications based on events from other services (e.g., new connection requests, post likes). Likely uses Kafka for event consumption.
* **`uploader-service`**: Handles file uploads (e.g., profile pictures, post attachments) potentially integrating with cloud storage like Cloudinary or Google Cloud Storage.

Communication between services primarily happens via REST APIs (through the gateway or direct Feign calls) and asynchronously via Apache Kafka for event-driven interactions. Each core service typically manages its own database.

## Features

* User Authentication (Sign up / Login with JWT)
* User Profiles
* Connection Management (Sending/Accepting Requests)
* Post Creation & Retrieval
* Post Liking
* Real-time Notifications (Event-driven via Kafka)
* API Gateway for unified access and security
* Service Discovery via Eureka
* File Upload capabilities

## Technologies Used

* **Languages/Frameworks:** Java (Specify JDK Version, e.g., 21+), Spring Boot, Spring Cloud (Gateway, Netflix Eureka, OpenFeign), Spring Data JPA, Spring Security, Spring Kafka
* **Database:** PostgreSQL (Typically one schema/database per service for local setup)
* **Messaging:** Apache Kafka
* **Build Tool:** Apache Maven
* **API Documentation:** Swagger/OpenAPI (via Springdoc likely)
* **Containerization:** Docker, Docker Compose
* **Orchestration:** Kubernetes (in `/k8s`)
* **Libraries:** JWT (jjwt), Lombok, etc.

## Prerequisites

* **Git:** For cloning the repository.
* **JDK:** Java Development Kit (*Specify required version, e.g., 21 or later*).
* **Maven:** Apache Maven build tool (or use the included Maven Wrapper `./mvnw`).
* **Docker & Docker Compose:** Required for running the application using Docker Compose. [Download Docker](https://www.docker.com/products/docker-desktop/).
* **PostgreSQL Server:** Required for the **Local Setup**. Needs a running instance.
* **`kubectl`:** Required for interacting with Kubernetes if using the Kubernetes deployment method.
* **(Optional) Kafka Instance:** For local development without Docker Compose, you might need a locally running Kafka instance. Docker Compose setup usually includes Kafka.
* **(Optional) PostgreSQL Client:** A tool like `psql` or pgAdmin to manage databases locally.

## Getting Started

### 1. Clone the Repository
**(Use your repo URL if different)**
```bash
git clone https://github.com/ARYANKUMAR1/Professional-Networking-Platform.git
cd Professional-Networking-Platform
