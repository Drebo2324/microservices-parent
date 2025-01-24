# Microservices
Spring Boot 3 Microservices

# Services
API-Gateway / Product Service / Order Service / Inventory Service / Notification Service / Frontend

# Tech Stack
- Spring MVC
- Spring Cloud
- Spring Security
- React
- MongoDB
- MySQL
- Kafka
- Zookeeper
- Avro
- Keycloak
- Testcontainers with Wiremock
- REST Assured
- Grafana Stack (Grafana, Loki, Tempo, Prometheus)
- Kubernetes

# Overview 
This is a project that consists of 5 different microservices: The API Gateway, Product Service, Order Service, Inventory Service, and the Notification Service. This is a simple e-commerce application where users can order products fetched from the Product Service. This project utilizes the microservices architectural patterns using both synchronous and event-driven communication.  

The API Gateway manages requests to the system. It uses Resilience4J to handle failures between service calls, and it uses Keycloak for security. The Product Service is where the frontend fetches the products from.  

The Order Service makes service calls to both the Inventory Service (synchronous) and the Notification Service (asynchronous). Kafka is used as a message broker. Once the Order Service has checked the Inventory Service for stock, it sends the relevant order data to the Kafka Topic to be consumed by the Notification Service where it uses that data to generate order confirmation emails.  

For Observability, the Grafana stack is used, implementing Prometheus for metrics collection, Loki for log aggregation, Tempo for distributed tracing, and Grafana to monitor it all. Kubernetes is used for deployment, service discovery, and load balancing. 

# How to run frontend app
> cd shop-front-ui
> npm install
> npm run start

# How to build the backend services
Run the following command to build and package the backend services into a docker container
> mvn spring-boot:build-image -DdockerPassword=<docker-account-password>

# How to run the backend services
Must have the following installed:
- Java 21
- Docker
- Kind Cluster - https://kind.sigs.k8s.io/docs/user/quick-start/#installation

Start the kind cluster

# Deploy the Infrastructure
Run the kubernetes/manifests/infrastructure.yaml to deploy the project infrastructure
> kubectl apply -f kubernetes/manifests/infrastructure.yaml

# Deploy the Services
Run the kubernetes/manifests/application.yaml to deploy the project services
> kubectl apply -f kubernetes/manifests/applications.yaml

# Access the API Gateway
To access the API Gateway, you must port-forward it to your local machine
> kubectl port-forward svc/api-gateway 9000:9000

# Access Keycloak Admin Console
To access the Keycloak admin console, you must port-forward it to to your local machine
> kubectl port-forward svc/keycloak 8080:8080

# Access the Grafana Dashboard
To access the Grafana Dashboard, you must port-forward it to to your local machine
> kubectl port-forward svc/grafana 3000:3000





