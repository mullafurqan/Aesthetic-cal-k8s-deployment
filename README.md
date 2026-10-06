# 🌸🖩 Aesthetic Calculator Web App

Welcome to my **Aesthetic Calculator Web Application**!  
This project combines **Python (Flask)** with **Bootstrap** and **JavaScript** to create a simple yet visually pleasing calculator with smooth animations and full keyboard support.

---

Here’s a quick look at the calculator in action:

![Preview Video](designs/AestheticCalculator.gif) 

---

## About This Project

The goal of this project was to make a **basic calculator** feel modern and engaging.  
From the **Aesthetic background** to the **interactive buttons**, every detail was designed to make the user experience smooth and aesthetically satisfying.  

This app is also a practical example of combining **Flask backend** with responsive **front-end design**.

---

## Key Features

- ✅ Modern gradient background with a clean UI  
- ✅ Fully responsive layout (desktop, tablet, mobile)  
- ✅ Interactive buttons with hover and click animations  
- ✅ Full keyboard support for faster calculations  
- ✅ Error handling for invalid operations  
- ✅ Lightweight and fast performance  

---

## Skills Gained

- Python Flask web development  
- Responsive design using Bootstrap  
- JavaScript event handling for UI interactivity  
- Keyboard event integration for web apps  
- CSS animations and gradient styling  
- Error handling in user-facing applications  

---

## Technologies & Tools Used

- **Python (Flask)** – Backend server  
- **Bootstrap** – Responsive design framework  
- **JavaScript** – Calculator logic & keyboard support  
- **HTML5 & CSS3** – Structure and aesthetic styling  

---
# Aesthetic Calculator – Kubernetes Deployment

<!-- Short description of the app (from your previous README) -->
A web-based aesthetic calculator, containerized with Docker and deployed on Kubernetes. The app runs on **port 5000**.

---

## 📖 About the Project
<!-- ===== PASTE YOUR PREVIOUS README CONTENT HERE ===== -->
<!-- Features, screenshots, tech stack, how the calculator works, etc. -->
<!-- ==================================================== -->

---

## 🧰 Tech Stack
- Application: `<your stack, e.g. Python Flask / Node.js>`
- Containerization: Docker
- Registry: Docker Hub
- Orchestration: Kubernetes (Deployment + Service)

---

## 📁 Project Structure
```
Aesthetic-cal-k8s-deployment/
├── app/                  # Application source code
├── Dockerfile            # Docker image definition
├── deployment.yaml       # Kubernetes Deployment manifest
├── service.yaml          # Kubernetes Service manifest
└── README.md
```

---

## 🐳 Docker

### Build the image
```bash
docker build -t <dockerhub-username>/aesthetic-cal:latest .
```

### Run locally
```bash
docker run -p 5000:5000 <dockerhub-username>/aesthetic-cal:latest
```
Open http://localhost:5000

### Push to Docker Hub
```bash
docker login
docker push <dockerhub-username>/aesthetic-cal:latest
```

Docker Hub image: `https://hub.docker.com/r/<dockerhub-username>/aesthetic-cal`

---

## ☸️ Kubernetes Deployment

### Prerequisites
- A running cluster (Minikube, kind, Docker Desktop, or a cloud cluster)
- `kubectl` configured to talk to the cluster

### deployment.yaml
Creates the pods running the Docker Hub image, exposing container port **5000**.
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: aesthetic-cal-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: aesthetic-cal
  template:
    metadata:
      labels:
        app: aesthetic-cal
    spec:
      containers:
        - name: aesthetic-cal
          image: <dockerhub-username>/aesthetic-cal:latest
          ports:
            - containerPort: 5000
```

### service.yaml
Exposes the deployment on port **5000**.
```yaml
apiVersion: v1
kind: Service
metadata:
  name: aesthetic-cal-service
spec:
  type: NodePort
  selector:
    app: aesthetic-cal
  ports:
    - port: 5000
      targetPort: 5000
      nodePort: 30007
```

### Deploy
```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

### Verify
```bash
kubectl get pods
kubectl get deployments
kubectl get services
```

---

## 🌐 Accessing the Application

**Minikube**
```bash
minikube service aesthetic-cal-service
```

**Port-forward (works on any cluster)**
```bash
kubectl port-forward service/aesthetic-cal-service 5000:5000
```
Then open http://localhost:5000

---

## 🔧 Useful Commands
```bash
kubectl logs <pod-name>                          # View logs
kubectl describe pod <pod-name>                  # Debug a pod
kubectl scale deployment aesthetic-cal-deployment --replicas=3
kubectl rollout restart deployment aesthetic-cal-deployment
kubectl delete -f service.yaml -f deployment.yaml   # Clean up
```

---

## 🚀 Deployment Workflow Summary
1. Built the Docker image from the `Dockerfile`
2. Pushed the image to Docker Hub
3. Wrote `deployment.yaml` and `service.yaml`
4. Applied both manifests with `kubectl`
5. Application is live on port **5000**

---

## 👤 Author
**mullafurqan** – [GitHub](https://github.com/mullafurqan)


