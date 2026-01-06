# Flask CI/CD to AWS EKS (Elasktic Kubernetes Service)
This Project demonstrates a complete CI/CD pipeline for a Flask application using Docker, GitHub Action and Amazon EKS(Kubernetes).

My goal for this project is to show how a modern DevOps Workflows can automaticly build, push and deploy an application to a managed Kubernetes Cluster in AWS.

# Deployment
1. Kubernetes deployment is handled via:
    `kubectl apply -f k8s/` 
2. Local deployment
     - `docker build -t flask-app .`
     - `docker run -p 5000:5000 flask-app`

# Overview

GitHub → GitHub Actions → Docker Hub → AWS EKS → Kubernetes Pods

**workflows**
1. code is pushed to `main`
2. Github Action
   - Builds a Docker image
   - Pushes the image to docker Hub
   - Deploys the application to AWS EKS using `kubectl`
3. Application runs inside a kubernetes Cluster (EKS)

# Tech stack
- Backend: Flask
- Containerization: Docker
- CI/CD: GitHub Actions
- Orchestration: Kubernetes
- Cloud Provider: AWS (Amazon Web Server)
- Kubernetes Service: Amazon EKS
- Kontainer Registry: Docker Hub

# Kubernets Deployment
The Flask App is deployd using standard Kubernetes manifest
1. Deployment
   - Defines the Flask Application
   - Use the Docker image from Docker Hub
2. Services
   - Exposes the application inside/outside the Cluster.

# AWS EKS setup
- EKS cluster created manuelly in AWS console
- public API endpoint enabled
- managed node grupp (EC2)
- IAM user with EKS permasion used by GitHub Actions
> The Cluster is not created in CI. CI only deploys to an existing cluster

**Notes:**

  EKS Cluster incur AWS cost when running. I closed/delete after everyting worked
  
  For learning porpuses, node group should be scaled down or delete when it not uses. 

# Author
  **Nasir Rahmanzada**
  
  *DevOps Engineer*
  
