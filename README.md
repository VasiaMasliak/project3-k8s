# Project 3 - Dockerized Web Application + Kubernetes (Minikube)

## 🎯 Goal
Demonstrate **containerization** and **orchestration** fundamentals by running a simple Flask web app inside a local Kubernetes cluster using **Docker + Minikube**.

---

## 🧱 Architecture
<pre>Localhost
├─ Docker → builds image (Flask app)
├─ Minikube → local Kubernetes cluster
│ ├─ Deployment (2 replicas)
│ └─ Service (NodePort :30080)
└─ Browser → access app via http://&lt;minikube-ip&gt;:30080</pre>

--- 

## 🧰 Tools & Technologies
- *Python Flask* (simple web app)
- *Docker* (containerization)
- *Kubernetes / Minikube* (orchestration)
- *kubectl* (management CLI)
- *YAML* (Kubernetes manifests)

---

## ✨ Key Features
*✅ Containerized Flask app (Dockerfile)*

*✅ Kubernetes Deployment (2 replicas)*

*✅ NodePort Service (exposes port `30080`)*

*✅ Local build and orchestration with Minikube*

*✅ Scaling and troubleshooting via `kubectl`*

---

## 📂 Folder Structure
<pre>├── README.md
├── app
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
└── k8s
    ├── deployment.yaml
    └── service.yaml
</pre>

## 🚀 Setup & Deployment

### 1️⃣ Start Minikube
>Make sure Docker Desktop is running.

**minikube start --driver=docker**

### 2️⃣ Point Docker CLI to Minikube
>Build images inside the Minikube Docker daemon:

**eval $(minikube docker-env)**

### 3️⃣ Build the Docker image
**docker build -t cicd:local ./app**

### 4️⃣ Deploy to Kubernetes
**kubectl apply -f k8s/deployment.yaml**

**kubectl apply -f k8s/service.yaml**

### 5️⃣ Verify resources
**kubectl get pods -l app=test-app**

**kubectl get svc test-svc**

### 6️⃣ Access the app
**minikube service test-svc**
>or manually 

**curl http://&lt;minikube-ip&gt;:30080**

>Expected output:

*Hello CICD*

## 🔄 Scaling
**kubectl scale deployment test-app --replicas=5**

**kubectl get pods -l app=test-app**

## 🛑 Stopping and Cleaning Up
> Option 1 - Pause the app(best practice):

**kubectl scale deployment test-app --replicas=0**

> Option 2 - Remove resources:

**kubectl delete -f k8s/service.yaml**

**kubectl delete -f k8s/deployment.yaml**

> Option 3 - Stop or delete the whole cluster:

**minikube stop**

**minikube delete**

## 🧠 Skill Demonstrated
* Docker image creation and optimization
* Kubernetes deployments, services, scaling
* YAML manifest authoring
* Local orchestration and debugging with Minikube
* Container lifecycle management






