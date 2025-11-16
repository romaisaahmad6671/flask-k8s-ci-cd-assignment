 1. Project Overview

This project implements a fully automated CI/CD pipeline:

🔹 Continuous Integration (GitHub Actions)

Triggered on every push or pull request:

Install dependencies

Run Flake8 linting

Run PyTest

Build Docker image

Provide instant feedback to developers

CI pipeline ensures code quality and avoids breaking changes from entering the repository.

🔹 Continuous Delivery (Jenkins Pipeline)

Triggered on updates to the main branch:

Clone the repository

(Simulated) Docker build inside Jenkins

Apply Kubernetes manifests (Deployment, Service)

Verify rollout using:

kubectl rollout status
kubectl get pods
kubectl get svc


Display deployment logs and status

This guarantees that every change pushed to main is automatically deployed into the Kubernetes cluster.

 Kubernetes Features Used
1. Deployment

Runs multiple replicas of the Flask app

Ensures self-healing (restarts failed pods)

Rolling updates (zero-downtime deployment)

2. Service (NodePort)

Exposes the application outside the cluster

Distributes traffic across replicas

3. Horizontal Pod Autoscaler (HPA)

Automatically scales replicas based on CPU load

Requires Metrics Server

Example:

kubectl autoscale deployment flask-app --min=1 --max=5 --cpu-percent=50

4. Rolling Updates

Deploys new versions without downtime

Uses:

kubectl rollout status
kubectl rollout history

5. Load Balancing

Built-in load balancing between multiple Flask pods

 2. Run the Application Locally with Docker
Build Docker Image
docker build -t flask-app .

Run Container
docker run -p 5000:5000 flask-app


Visit:
 http://localhost:5000

 3. Deploy Manually to Kubernetes (Without Jenkins)
Start Minikube
minikube start

Apply Manifests
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml

Check Deployment
kubectl get pods
kubectl get svc
kubectl rollout status deployment/flask-app

 4. Automated Deployment with Jenkins

The Jenkins pipeline (Jenkinsfile) performs:

Stage 1 — Checkout Code

Clones latest code from main.

Stage 2 — Build Docker Image (Simulated)

Inside Jenkins container Docker is unavailable, so build is simulated.

Stage 3 — Deploy to Kubernetes
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml

Stage 4 — Verify Deployment
kubectl rollout status deployment/flask-app
kubectl get pods
kubectl get svc

Outcome

✔ Fully automated CD
✔ Zero-downtime deployments
✔ Jenkins → Kubernetes pipeline validated

 5. Auto-Scaling & Load Balancing
Enable HPA
kubectl autoscale deployment flask-app --min=1 --max=5 --cpu-percent=50

Simulate Load
kubectl run load-generator --image=busybox -- /bin/sh -c "while true; do wget -q -O- http://flask-service:5000; done"

Check Scaling
kubectl get hpa
kubectl get pods


Kubernetes automatically increases or decreases the number of pods based on demand.

 6. Summary of the CI/CD Workflow
Developer Pushes Code → GitHub Actions → Lint + Test + Docker Build
         ↓
      Merge to main
         ↓
       Jenkins CI/CD Pipeline
         ↓
Auto Deploy to Kubernetes (Minikube)
         ↓
Rolling Update → Load Balancing → Auto-Scaling

 7. Final Deliverables Included

✔ Complete CI/CD workflow
✔ Kubernetes deployment + autoscaling
✔ Jenkins pipeline
✔ Full README documentation
✔ Screenshots for GitHub Actions, Jenkins pipeline & Kubernetes resources