#  E-Cart Application on Kubernetes

# Overview
This repository contains the deployment configurations and documentation for a simulated e-commerce application deployed in a Kubernetes environment. The application consists of a frontend (React-based web app), backend API (Node.js microservices), MongoDB cluster for data persistence, and RabbitMQ for asynchronous order processing.

# Table of Contents

- Components
- Getting Started
- Prerequisites
- Configuration
- Deployment
- Observability and Scaling
- Monitoring and Logging
- Autoscaling
- Security and Compliance

# Components

1. Frontend
    - React-based web application served by Nginx.

2. Backend API
    - Set of Node.js microservices handling various business operations.

3. Database
    - MongoDB cluster for data persistence.

4. Message Queue
    - RabbitMQ for handling order processing asynchronously.

# Getting Started

## Prerequisites
- Docker
- kubectl
- Setup a cluster with kubeadm. (Setup the cluster on any cloud provider as per convenience)

## Configuration

1. Clone the Repository:

```
git clone https://github.com/your-username/k8s-pe-sketch.git
cd k8s-pe-sketch
```

2. Configure Application:

Frontend Service calling Backend API:
```
// Frontend code
const backendApiUrl = "http://backend-api-service:3000";
// Make API requests to backendApiUrl
```

Backend API connecting to MongoDB:

```
// Backend API code
const mongoDbUrl = "mongodb://mongodb-service:27017";
// Connect to MongoDB using mongoDbUrl
```

Backend API sending messages to RabbitMQ:

```
// Backend API code
const rabbitMqUrl = "rabbitmq-service:5672";
// Connect to RabbitMQ using rabbitMqUrl
```

## Deployment

1. Deploy Kubernetes Resources:

```
kubectl apply -f deployments/
```

2. Expose Frontend with Ingress:

```
kubectl apply -f ingress.yaml
```

3. Verify Deployment:

```
kubectl get pods,svc,deployments
```

# Observability and Scaling

## Monitoring and Logging

1. Prometheus and Grafana:
- Deploy Prometheus and Grafana for monitoring.
```
kubectl apply -f monitoring/
```
2. ELK Stack
- Deploy ELK Stack for centralized logging.
```
kubectl apply -f logging/
```

## Autoscaling

1. Horizontal Pod Autoscaling (HPA):

- Implement HPA for frontend and backend services
```
kubectl apply -f autoscaling/hpa/
```

# Security and Compliance

1. Pod Security Policies (PSP):

- Ensure Pod Security Policies are applied to restrict pod privileges.
```
kubectl apply -f security/pod-security-policies/
```

2. Gatekeeper
- Use gatekeeper for more advanced policy enforcement
```
kubectl apply -f security/gatekeeper/
```
