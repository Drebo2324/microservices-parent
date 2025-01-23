# Microservices
Spring Boot 3 Microservices

# Services
API-Gateway / Product Service / Order Service / Inventory Service / Notification Service / Frontend

# Tech Stack
- Spring Boot
- React
- MongoDB
- MySQL
- Kafka
- Keycloak
- Testcontainers with Wiremock
- Grafana Stack (Grafana, Loki, Tempo, Prometheus)
- API Gateway using Spring Cloud Gateway MVC
- Kubernetes

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





