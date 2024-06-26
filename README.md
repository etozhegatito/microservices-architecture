# Microservices Architecture

A comprehensive final project designed to showcase the power and flexibility of Docker and Kubernetes by creating a fully scalable microservices architecture. This repository demonstrates containerization, orchestration, health checks, and more.

## Getting Started

### Prerequisites
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)

### Building and Running

1. **Build the Containers**  
   Start by building all the containers for the services:
   ```bash
   docker-compose build
   ```

2. **Start All Services**  
   Spin up the containers for all services and check:
   ```bash
   docker-compose up
   docker-compose ps

   ```

3. **Access the Services**  
   Visit the following URLs to interact with the services directly:
    - [Users Service](http://localhost:8080/)
    - [Orders Service](http://localhost:8081/)
    - [Products Service](http://localhost:8082/)

## Kubernetes Setup

1. **Start Minikube**  
   Begin by launching a Minikube cluster:
   ```bash
   minikube start
   ```

2. **Apply the Kubernetes Configurations**  
   Use `kubectl` to apply all the Kubernetes resources:
   ```bash
   kubectl apply -f k8s/orders-deployment.yaml
   kubectl apply -f k8s/orders-service.yaml
   kubectl apply -f k8s/orders-service-autoscaler.yaml
   kubectl apply -f k8s/products-deployment.yaml
   kubectl apply -f k8s/products-service.yaml
   kubectl apply -f k8s/products-service-autoscaler.yaml
   kubectl apply -f k8s/users-deployment.yaml
   kubectl apply -f k8s/users-service.yaml
   kubectl apply -f k8s/users-service-autoscaler.yaml
   ```

3. **Check Kubernetes Status**  
   Verify the status of your cluster resources (It is very important to follow everything step by step!):
   ```bash
  
   kubectl describe pods
   kubectl get nodes
   minikube addons enable metrics-server |or| minikube start --addons=metrics-server
   kubectl autoscale deployment orders-service --cpu-percent=75 --min=1 --max=6
   kubectl autoscale deployment products-service --cpu-percent=70 --min=1 --max=5
   kubectl autoscale deployment users-service --cpu-percent=80 --min=1 --max=10
   kubectl delete hpa orders-service-hpa
   kubectl delete hpa products-service-hpa
   kubectl delete hpa users-service-hpa
   kubectl get hpa
   kubectl get events
   kubectl get deployments
   kubectl get services
   ```

## Project Description

### Overview
In this final project, we'll explore the world of containerization and orchestration by implementing a comprehensive solution using Docker and Kubernetes. The primary goal is to design and deploy a scalable microservices architecture for a fictional application.

### Components

1. **Microservices Architecture Design**
    - Identify and define the microservices that will form the application.
    - Establish communication protocols and dependencies between the microservices.

2. **Containerization with Docker**
    - Create lightweight, portable containers for each microservice using Docker.
    - Utilize Docker Compose for local development and testing.

3. **Container Orchestration with Kubernetes**
    - Set up a Kubernetes cluster to manage container deployment, scaling, and operation.
    - Define Kubernetes deployment configurations for each microservice.
    - Implement services, ingresses, and other necessary resources to enable seamless communication.

4. **Scaling and Load Balancing**
    - Leverage Kubernetes' auto-scaling capabilities to dynamically adjust the number of running containers.
    - Utilize a load balancer to distribute traffic across multiple microservice instances.

5. **Health Checks and Self-Healing**
    - Implement health checks and define Kubernetes probes to monitor service health.
    - Demonstrate Kubernetes' self-healing by replacing unhealthy containers.

6. **Documentation and Demonstration**
    - Provide comprehensive documentation to set up the environment and deploy the application.
    - Create a demonstration highlighting the entire process of containerization and orchestration.

## Contributors

- Bakirbayev Sanzhar - 210103167
- Yerdali Akarys - 210103145
- Sanabek Yeldos - 210103116