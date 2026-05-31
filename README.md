# Go Web Application CI/CD and GitOps Deployment on AWS EKS

## Project Overview

This project demonstrates the implementation of modern DevOps practices for a Golang web application. The application is a simple website built using Go's `net/http` package to serve HTTP requests.

The primary objective is to automate the software delivery lifecycle, from code commit to deployment, using containerization, Continuous Integration (CI), Continuous Deployment (CD), Kubernetes, and GitOps principles.

## Key Features

* Multi-stage Docker builds
* Containerized Go application
* Automated CI pipeline using GitHub Actions
* Docker image publishing to Docker Hub
* Helm-based Kubernetes deployment
* GitOps workflow using Argo CD
* Deployment on Amazon EKS

## Architecture Diagram

![Architecture Diagram](https://github.com/user-attachments/assets/45f4ef12-c5b5-4247-9d43-356b5dfb671b)

## Docker Multi-Stage Build

A multi-stage Docker build is used to create lightweight and secure container images.

Benefits include:

* Reduced image size
* Faster deployments
* Improved security
* Removal of unnecessary build dependencies from the final image

## Containerization

The application is containerized using Docker, ensuring consistent execution across development, testing, and production environments.

### Build Docker Image

```bash
docker build -t <your-docker-username>/go-web-app .
```

### Run Docker Container

```bash
docker run -p 8080:8080 <your-docker-username>/go-web-app
```

### Push Image to Docker Hub

```bash
docker push <your-docker-username>/go-web-app
```

## Continuous Integration (CI)

GitHub Actions is used to automate the build and validation process.

The CI pipeline performs the following tasks:

* Checkout source code
* Build the Go application
* Run unit tests
* Perform code quality checks
* Build Docker image
* Push Docker image to Docker Hub

This ensures that every code change is validated before deployment.

## Continuous Deployment (CD)

Argo CD is used to implement GitOps-based Continuous Deployment.

Deployment workflow:

1. Developer pushes code to GitHub.
2. GitHub Actions builds and pushes a new Docker image.
3. Helm chart image tag is automatically updated.
4. Changes are committed back to GitHub.
5. Argo CD detects the repository change.
6. Argo CD synchronizes the Kubernetes cluster.
7. The latest application version is deployed automatically.

## Technology Stack

* Golang
* Docker
* GitHub Actions
* Docker Hub
* Kubernetes
* Helm
* Argo CD
* Amazon EKS
* GitOps

## Outcome

This project demonstrates an end-to-end DevOps workflow by automating application build, testing, containerization, image publishing, and deployment to Kubernetes using GitOps principles.
