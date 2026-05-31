# DevOpsified Go Web Application

## Overview

This project demonstrates the implementation of modern DevOps practices for a Golang web application.

The application is a simple website built using Go's `net/http` package to serve HTTP requests. The primary goal of this project is to automate the entire software delivery lifecycle, from development to deployment, using containerization, Kubernetes, CI/CD pipelines, Helm, and GitOps.

## Project Objectives

* Containerize the Go application using Docker
* Implement multi-stage Docker builds
* Deploy the application on Kubernetes
* Package Kubernetes manifests using Helm
* Automate Continuous Integration using GitHub Actions
* Automate Continuous Deployment using ArgoCD
* Deploy and manage workloads on Amazon EKS
* Follow GitOps deployment practices

## Architecture

![Architecture Diagram](https://github.com/user-attachments/assets/45f4ef12-c5b5-4247-9d43-356b5dfb671b)

## Technology Stack

| Category                | Technology               |
| ----------------------- | ------------------------ |
| Programming Language    | Golang                   |
| Containerization        | Docker                   |
| Container Registry      | Docker Hub               |
| CI Pipeline             | GitHub Actions           |
| Container Orchestration | Kubernetes               |
| Kubernetes Packaging    | Helm                     |
| GitOps                  | ArgoCD                   |
| Cloud Platform          | AWS EKS                  |
| Ingress Controller      | NGINX Ingress Controller |

## Project Workflow

### 1. Application Development

* Developed and tested the Go web application locally.
* Verified application functionality using the local server.

```bash
go run main.go
```

The application runs on:

```text
http://localhost:8080/courses
```

---

### 2. Containerization

Created a multi-stage Dockerfile to optimize image size and improve security.

Benefits:

* Smaller image size
* Faster deployments
* Reduced attack surface
* Separation of build and runtime environments

Build Docker image:

```bash
docker build -t <your-dockerhub-username>/go-web-app .
```

Run Docker container:

```bash
docker run -p 8080:8080 <your-dockerhub-username>/go-web-app
```

Push image to Docker Hub:

```bash
docker push <your-dockerhub-username>/go-web-app
```

---

### 3. Kubernetes Deployment

Created Kubernetes manifests for:

* Deployment
* Service
* Ingress

These resources allow the application to run and be exposed inside the Kubernetes cluster.

---

### 4. AWS EKS Setup

Configured the AWS environment by:

* Creating an IAM user
* Configuring AWS CLI
* Installing kubectl
* Connecting kubectl with EKS
* Creating and configuring the EKS cluster

---

### 5. NGINX Ingress Configuration

Installed NGINX Ingress Controller and configured ingress resources.

Tasks performed:

* Installed NGINX Ingress Controller
* Applied Kubernetes manifests
* Verified LoadBalancer creation
* Configured DNS mapping

This enabled external access to the application.

---

### 6. Helm Integration

Migrated Kubernetes manifests into Helm charts.

Tasks performed:

* Installed Helm
* Created Helm chart structure
* Moved Deployment, Service, and Ingress manifests into templates
* Tested deployments using Helm
* Removed standalone Kubernetes manifests after successful validation

Benefits:

* Reusable deployments
* Environment-specific configuration
* Easier application upgrades

---

### 7. Continuous Integration (CI)

Implemented CI using GitHub Actions.

The CI pipeline performs:

* Source code checkout
* Go application build
* Unit testing
* Code quality checks
* Docker image build
* Docker image push to Docker Hub
* Automatic Helm chart image tag update

Workflow:

```text
Code Push
    ↓
Build
    ↓
Test
    ↓
Lint
    ↓
Docker Build
    ↓
Docker Push
    ↓
Update Helm Chart
```

---

### 8. Continuous Deployment (CD)

Implemented GitOps-based deployment using ArgoCD.

Tasks performed:

* Installed ArgoCD
* Retrieved initial admin credentials
* Connected GitHub repository
* Created ArgoCD Application
* Enabled automatic synchronization

---

### 9. GitOps Deployment Flow

```text
Developer Pushes Code
        │
        ▼
GitHub Actions
        │
        ▼
Build & Test Application
        │
        ▼
Build Docker Image
        │
        ▼
Push Image to Docker Hub
        │
        ▼
Update Helm Chart Tag
        │
        ▼
Push Changes to GitHub
        │
        ▼
ArgoCD Detects Changes
        │
        ▼
Synchronizes EKS Cluster
        │
        ▼
Application Updated Automatically
```

## CI/CD Pipeline Features

* Automated build process
* Automated testing
* Automated Docker image creation
* Automated Docker Hub publishing
* Automated Helm chart updates
* Automated Kubernetes deployment
* GitOps-driven delivery workflow

## Running the Application Locally

Clone the repository:

```bash
git clone <repository-url>
```

Navigate to the project directory:

```bash
cd go-web-app
```

Run the application:

```bash
go run main.go
```

Open:

```text
http://localhost:8080/courses
```

## Key Learnings

* Docker multi-stage builds
* Kubernetes deployments and services
* NGINX Ingress Controller
* AWS EKS administration
* Helm chart management
* GitHub Actions CI pipelines
* ArgoCD GitOps workflows
* Automated application delivery

## Conclusion

This project demonstrates an end-to-end DevOps implementation for a Golang web application using Docker, Kubernetes, Helm, GitHub Actions, ArgoCD, and Amazon EKS. It showcases modern CI/CD and GitOps practices commonly used in production-grade cloud-native environments.
