# MERN E-Commerce Platform - DevOps Deployment Project

## Project Overview

This project demonstrates the deployment of a MERN-based E-Commerce application using a complete DevOps workflow on AWS.

The application is containerized using Docker, integrated with Jenkins CI/CD, deployed on a self-managed Kubernetes cluster, and monitored using Prometheus and Grafana.

The goal of this project was to simulate a production-style deployment environment while learning core DevOps tools and practices.

---

## Architecture

```text
GitHub Repository
        │
        ▼
Jenkins CI/CD
        │
        ▼
Docker Build
        │
        ▼
Docker Hub Registry
        │
        ▼
Kubernetes Cluster
        │
 ┌──────┼───────────────┐
 │      │               │
 ▼      ▼               ▼
MERN   MongoDB        Redis
App      Pod           Pod
 │
 ▼
Ingress
 │
 ▼
Application Access

Monitoring Stack
 ├── Prometheus
 └── Grafana
```

---

## Infrastructure Setup

### AWS EC2 Instances

| Instance | Purpose                |
| -------- | ---------------------- |
| EC2-1    | Jenkins Server         |
| EC2-2    | Kubernetes Master Node |
| EC2-3    | Kubernetes Worker Node |

### Operating System

* Ubuntu Server

---

## Technology Stack

### Cloud & Infrastructure

* AWS EC2
* Linux (Ubuntu)

### CI/CD

* Jenkins
* GitHub

### Containerization

* Docker
* Docker Hub

### Container Orchestration

* Kubernetes (kubeadm)

### Application Services

* Node.js
* React.js
* MongoDB
* Redis

### Monitoring

* Prometheus
* Grafana

### Networking

* Kubernetes Services
* NGINX Ingress Controller

---

## CI/CD Pipeline Workflow

The deployment pipeline follows the below workflow:

```text
Developer Push
       │
       ▼
GitHub Repository
       │
       ▼
Jenkins Pipeline
       │
       ├── Build Docker Image
       ├── Push Image to Docker Hub
       ├── Update Kubernetes Deployment
       └── Verify Rollout
       │
       ▼
Kubernetes Cluster
```

---

## Kubernetes Components

### Namespace

```text
ecommerce
```

### Deployments

* ecommerce-app
* mongodb
* redis

### Services

* ecommerce-service
* mongodb-service
* redis-service

### Ingress

* NGINX Ingress Controller

---

## Monitoring Setup

Monitoring was implemented using:

### Prometheus

Used for:

* Cluster Monitoring
* Node Monitoring
* Pod Monitoring
* Resource Utilization Tracking

### Grafana

Used for visualizing:

* CPU Usage
* Memory Usage
* Pod Health
* Cluster Metrics
* Node Metrics

---

## Deployment Process

### 1. Clone Repository

```bash
git clone <repository-url>
```

### 2. Build Docker Image

```bash
docker build -t image-name .
```

### 3. Push Image to Docker Hub

```bash
docker push image-name
```

### 4. Jenkins CI/CD

Jenkins automatically:

* Pulls source code from GitHub
* Builds Docker image
* Pushes image to Docker Hub
* Updates Kubernetes deployment
* Performs rolling update

### 5. Kubernetes Deployment

Application is deployed on Kubernetes using:

* Deployment
* Service
* Ingress

---

## Monitoring Verification

Grafana dashboards were used to monitor:

* Kubernetes Cluster
* Worker Node
* Application Pods
* MongoDB Pod
* Redis Pod

---

## Project Highlights

* Built a self-managed Kubernetes cluster using kubeadm.
* Configured Jenkins for Continuous Integration and Continuous Deployment.
* Containerized MERN application using Docker.
* Automated image publishing to Docker Hub.
* Deployed application using Kubernetes Deployments and Services.
* Configured MongoDB and Redis as Kubernetes workloads.
* Implemented Kubernetes Ingress for application routing.
* Integrated Prometheus and Grafana for monitoring and observability.
* Performed troubleshooting for Kubernetes networking, DNS resolution, pod failures, and service connectivity.

---

## Learning Outcomes

This project provided hands-on experience with:

* Linux Administration
* Git & GitHub
* Docker
* Docker Hub
* Jenkins
* Kubernetes
* CI/CD Automation
* Application Deployment
* Monitoring & Observability
* AWS Infrastructure Management
* Kubernetes Troubleshooting

---

## Future Improvements

Possible future enhancements:

* HTTPS with Let's Encrypt
* Custom Domain Integration
* Kubernetes Secrets Management
* Horizontal Pod Autoscaling (HPA)
* Centralized Logging using ELK Stack
* Multi-Environment Deployments (Dev, QA, Production)

---

## Author

Raj Patel

DevOps | Cloud | Kubernetes | AWS
