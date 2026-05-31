# Install Argo CD

This guide explains how to install Argo CD on a Kubernetes cluster and access its web interface.

## Prerequisites

Ensure the following tools are installed and configured:

* Kubernetes Cluster (EKS, Minikube, Kind, etc.)
* kubectl
* AWS CLI (for EKS users)

Verify cluster connectivity:

```bash
kubectl get nodes
```

---

## Create Argo CD Namespace

Create a dedicated namespace for Argo CD:

```bash
kubectl create namespace argocd
```

---

## Install Argo CD

Deploy Argo CD using the official installation manifests:

```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Verify the installation:

```bash
kubectl get pods -n argocd
```

Wait until all pods are in the `Running` state.

---

## Expose the Argo CD Server

By default, the Argo CD server is exposed as a ClusterIP service.

Convert it to a LoadBalancer service to access the UI externally.

### Linux / macOS

```bash
kubectl patch svc argocd-server -n argocd -p '{"spec":{"type":"LoadBalancer"}}'
```

### Windows PowerShell

```bash
kubectl patch svc argocd-server -n argocd -p '{\"spec\":{\"type\":\"LoadBalancer\"}}'
```

---

## Get the LoadBalancer Endpoint

Retrieve the external endpoint:

```bash
kubectl get svc argocd-server -n argocd
```

Example output:

```text
NAME            TYPE           CLUSTER-IP      EXTERNAL-IP                                                               PORT(S)
argocd-server   LoadBalancer   10.100.12.15    a1b2c3d4e5f6.ap-south-1.elb.amazonaws.com   80:32000/TCP,443:32001/TCP
```

Open the `EXTERNAL-IP` value in your browser.

---

## Get the Initial Admin Password

Retrieve the default Argo CD admin password:

```bash
kubectl -n argocd get secret argocd-initial-admin-secret \
-o jsonpath="{.data.password}" | base64 --decode
```

For Windows PowerShell:

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"
```

Copy the encoded value and decode it using Base64.

---

## Login to Argo CD

Default credentials:

```text
Username: admin
Password: <retrieved-password>
```

After logging in, you can connect your Git repository and create Argo CD Applications for GitOps-based deployments.

---

## Verify Installation

Check all Argo CD resources:

```bash
kubectl get all -n argocd
```

Verify pods:

```bash
kubectl get pods -n argocd
```

Verify services:

```bash
kubectl get svc -n argocd
```

All resources should be in a healthy state before proceeding with application deployment.
