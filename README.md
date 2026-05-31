# DevOpsified Go Web Application

## Overview

A production-ready Golang web application demonstrating Docker, Kubernetes, Helm, GitHub Actions, ArgoCD, GitOps, and Amazon EKS.

This project showcases how a traditional Go web application can be transformed into a cloud-native application using modern DevOps practices. It covers the complete application lifecycle, including containerization, Kubernetes deployment, CI/CD automation, GitOps workflows, and cloud infrastructure management.

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

## End-to-End DevOps Flow

```text
Developer
    ↓
GitHub Repository
    ↓
GitHub Actions
    ↓
Build & Test
    ↓
Docker Image Build
    ↓
Docker Hub
    ↓
Helm Chart Update
    ↓
Git Repository Update
    ↓
ArgoCD
    ↓
Amazon EKS
    ↓
Application Deployment
```

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

## Features

* Multi-stage Docker image builds
* Kubernetes Deployment, Service, and Ingress
* AWS EKS cluster deployment
* Helm chart packaging
* GitHub Actions CI pipeline
* ArgoCD GitOps deployment
* Automated Docker image publishing
* Automated Helm chart image tag updates
* Automated Kubernetes synchronization
* Cloud-native application delivery

## Project Structure

```text
.
├── .github/
│   └── workflows/
│       └── ci-cd.yaml
├── helm/
│   └── go-web-app-chart/
├── ingress-controller/
│   └── nginx/
├── gitops/
│   └── argocd/
├── static/
├── templates/
├── Dockerfile
├── main.go
└── README.md
```

## Project Workflow

### 1. Application Development

* Developed and tested the Go web application locally.
* Verified application functionality before containerization.

Run locally:

```bash
go run main.go
```

Access the application:

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

* Creating IAM users and permissions
* Configuring AWS CLI
* Installing and configuring kubectl
* Creating an Amazon EKS cluster
* Connecting kubectl to the EKS cluster

---

### 5. NGINX Ingress Controller

Installed and configured the NGINX Ingress Controller.

Tasks performed:

* Installed NGINX Ingress Controller
* Applied Kubernetes manifests
* Verified LoadBalancer creation
* Configured ingress routing

This enabled external access to the application running inside the cluster.

---

### 6. Helm Integration

Migrated Kubernetes manifests into Helm charts.

Tasks performed:

* Installed Helm
* Created Helm chart structure
* Converted Kubernetes manifests into templates
* Tested deployments using Helm
* Managed environment-specific configurations

Benefits:

* Reusable deployments
* Version-controlled releases
* Easier upgrades and rollbacks

---

### 7. Continuous Integration (CI)

Implemented CI using GitHub Actions.

Pipeline stages:

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

* Automated application builds
* Automated testing and validation
* Docker image creation and publishing
* Helm chart version updates
* GitOps-driven deployments
* Automatic Kubernetes synchronization
* Reduced manual deployment effort

## Running the Application Locally

Clone the repository:

```bash
git clone <repository-url>
```

Navigate to the project directory:

```bash
cd DevOpsified-Go-Web-Application
```

Run the application:

```bash
go run main.go
```

Open:

```text
http://localhost:8080/courses
```

## Resume Highlights

* Implemented an end-to-end CI/CD pipeline using GitHub Actions.
* Containerized a Golang application using Docker multi-stage builds.
* Deployed workloads on Amazon EKS using Kubernetes and Helm.
* Implemented GitOps workflows using ArgoCD.
* Automated Docker image publishing and Kubernetes deployments.
* Configured NGINX Ingress Controller for external traffic routing.
* Managed cloud-native deployments using AWS EKS.

## Key Learnings

* Docker multi-stage builds
* Kubernetes deployments and services
* NGINX Ingress Controller
* AWS EKS administration
* Helm chart management
* GitHub Actions CI pipelines
* ArgoCD GitOps workflows
* Cloud-native deployment strategies
* End-to-end DevOps automation

## Conclusion

This project demonstrates how a traditional Golang web application can be transformed into a cloud-native, production-ready system using modern DevOps practices. The implementation covers containerization, Kubernetes orchestration, CI/CD automation, GitOps deployment strategies, and cloud infrastructure management on AWS EKS.
