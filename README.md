Flask Kubernetes CI/CD Pipeline with GitHub Actions & Jenkins

This project demonstrates a complete CI/CD pipeline for a Flask application deployed on Kubernetes, using:

GitHub Actions for Continuous Integration (CI)

Jenkins for Continuous Delivery (CD)

Docker for containerization

Kubernetes (Minikube) for deployment, scaling & load balancing

Horizontal Pod Autoscaler for auto-scaling

 1. Project Overview

This project implements an end-to-end CI/CD pipeline:

 GitHub Actions

Runs automatically on every push:

Install dependencies

Flake8 linting

PyTest

Docker build

 Jenkins Pipeline

Triggered on changes to main:

Clones repo

(Simulates) Docker Build

Deploys to Kubernetes

Runs rollout verification

Shows live deployment status

 Kubernetes Features Used

Deployments (replicas & rolling updates)

Services (NodePort)

Horizontal Pod Autoscaler (HPA)

Metrics Server

Automatic Rollouts

Load balancing between pods

You deploy, update, scale, and test everything with automation.