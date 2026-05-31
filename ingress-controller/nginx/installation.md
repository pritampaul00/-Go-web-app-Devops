# Install NGINX Ingress Controller on AWS EKS

This guide explains how to install and verify the NGINX Ingress Controller on an Amazon EKS cluster.

## Prerequisites

Ensure the following requirements are met:

* Amazon EKS cluster is running
* kubectl is installed and configured
* AWS CLI is configured
* Cluster connectivity is verified

Verify access to the cluster:

```bash
kubectl get nodes
```

---

## Install NGINX Ingress Controller

Deploy the official NGINX Ingress Controller manifests for AWS:

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.11.1/deploy/static/provider/aws/deploy.yaml
```

---

## Verify Installation

Check that the NGINX Ingress Controller pods are running:

```bash
kubectl get pods -n ingress-nginx
```

Expected output:

```text
NAME                                        READY   STATUS    RESTARTS   AGE
ingress-nginx-controller-xxxxx              1/1     Running   0          2m
```

---

## Verify Services

List the services created by the installation:

```bash
kubectl get svc -n ingress-nginx
```

Example:

```text
NAME                                 TYPE           EXTERNAL-IP
ingress-nginx-controller             LoadBalancer   a1b2c3d4.ap-south-1.elb.amazonaws.com
```

The LoadBalancer service provisions an AWS Elastic Load Balancer automatically.

---

## Retrieve the Load Balancer Endpoint

Retrieve the external endpoint:

```bash
kubectl get svc ingress-nginx-controller -n ingress-nginx
```

Example output:

```text
NAME                       TYPE           EXTERNAL-IP
ingress-nginx-controller   LoadBalancer   a1b2c3d4.ap-south-1.elb.amazonaws.com
```

This endpoint will be used by your Kubernetes Ingress resources to route external traffic to applications running inside the cluster.

---

## Verify Controller Deployment

Check the deployment status:

```bash
kubectl get deployment -n ingress-nginx
```

View controller logs:

```bash
kubectl logs -n ingress-nginx deployment/ingress-nginx-controller
```

---

## Validate Installation

Ensure all resources are healthy:

```bash
kubectl get all -n ingress-nginx
```

All pods should be in the `Running` state and the controller service should have an assigned external Load Balancer endpoint.

---

## Next Steps

After installing the NGINX Ingress Controller:

1. Create Kubernetes Deployment manifests.
2. Create Kubernetes Service manifests.
3. Create Ingress resources.
4. Apply the manifests to the cluster.
5. Access the application through the Load Balancer endpoint.
6. Configure DNS mapping if required.
