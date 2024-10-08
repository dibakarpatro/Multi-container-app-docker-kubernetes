# Multi-Container Application Deployment with Docker Compose and Kubernetes

This repository contains the deliverables for the **Multi-Container Application Deployment** task assigned by **Techdome**. The task involves deploying a full-stack application (frontend, backend, and database) using **Docker Compose** and **Kubernetes**. Below, you’ll find the architecture details, deployment strategy, and instructions for building and deploying the application.

## Repository Structure

This repository contains two key components:
- **Backend**: [Techdome-backend](https://github.com/Anand-1432/Techdome-backend)
- **Frontend**: [Techdome-frontend](https://github.com/Anand-1432/Techdome-frontend)

### Key Tools Used:
- **Docker**: For containerizing the application.
- **Docker Compose**: To define and manage multi-container applications.
- **Kubernetes**: For deploying and managing the application in a local Kubernetes cluster.
- **Minikube**: For setting up a local Kubernetes environment.

---

## Application Architecture

The multi-container application consists of the following services:

1. **Frontend Container**:
   - A user-facing web application that communicates with the backend API.
   - Built with modern web technologies (e.g., React, Angular, or Vue).
   
2. **Backend Container**:
   - A RESTful API service that handles business logic and connects to the database.
   - Built with a framework like Node.js, Flask, or Django.
   
3. **Database Container**:
   - A database service to persist application data.
   - Uses a relational or NoSQL database like MySQL, PostgreSQL, or MongoDB.

These three containers are interconnected, forming a complete full-stack application.

---

## Docker Compose Setup

The **Docker Compose** file is used to define and manage the application’s containers. It specifies how each container (frontend, backend, and database) is built, networked, and run.

### Key Sections of the Docker Compose File:
- **Services**: Defines the frontend, backend, and database containers.
- **Networks**: Configures container networking to enable inter-service communication.
- **Volumes**: Configures persistent storage for the database container.
- **Ports**: Maps the internal container ports to the host machine for accessibility.

#### To Build and Start the Application with Docker Compose:
1. Clone the repositories:
    ```bash
    git clone https://github.com/Anand-1432/Techdome-backend
    git clone https://github.com/Anand-1432/Techdome-frontend
    ```
2. Run Docker Compose:
    ```bash
    docker-compose up --build
    ```
3. Access the frontend application in the browser at `http://localhost:<frontend_port>`.

---

## Kubernetes Deployment

### Kubernetes Deployment Strategy:
The application is deployed on a local Kubernetes cluster (using **Minikube**) for container orchestration. The deployment involves creating **Pods**, **Services**, and **Deployments** for the frontend, backend, and database components.

### Kubernetes Manifests:
- **Deployment Manifests**: YAML files that define the deployment of each container as a Pod.
- **Service Manifests**: YAML files that define how services within the Kubernetes cluster communicate.

### To Deploy the Application to Kubernetes:
1. Start Minikube:
    ```bash
    minikube start
    ```
2. Apply the Kubernetes manifests:
    ```bash
    kubectl apply -f kubernetes-manifests/
    ```
3. Verify the Pods and Services are running:
    ```bash
    kubectl get pods
    kubectl get services
    ```
4. Access the frontend application via the Minikube service IP:
    ```bash
    minikube service <frontend-service-name>
    ```

---

## Deployment Strategy

1. **Local Development**: For local development and testing, Docker Compose is used to spin up all the containers and connect them via a shared network.
2. **Kubernetes Deployment**: Once the application is tested locally, it is deployed to a local Kubernetes cluster using **Minikube**. Kubernetes handles the orchestration, load balancing, and scaling of the containers.
3. **Networking**: The frontend and backend communicate via a private Docker/Kubernetes network. The database container is also reachable from the backend container.

---

## Deliverables

1. **Docker Compose File**: Defines the multi-container architecture.
2. **Kubernetes Deployment Manifests**: (Optional) YAML files for deploying the application in Kubernetes.
3. **Documentation**: This README file provides an overview of the application architecture and the deployment process.

---

## Conclusion

This multi-container application successfully demonstrates deploying a full-stack system using Docker Compose and Kubernetes. The setup ensures scalability, modularity, and easy orchestration of the application services.
