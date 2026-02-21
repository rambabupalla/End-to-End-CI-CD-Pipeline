# 🚀 End-to-End CI/CD Pipeline using Jenkins, Docker & Kubernetes

## 📌 Project Overview
This project demonstrates a complete CI/CD pipeline for Static web application.
The pipeline automates build, containerization, image push, and Kubernetes deployment.

---

## 🏗 Architecture Flow
GitHub → Jenkins → Maven → Docker → DockerHub → Kubernetes Cluster

---

## 🔧 Tools & Technologies Used
- Jenkins (Pipeline as Code)
- Maven
- Docker
- DockerHub
- Kubernetes
- SSH Publisher Plugin
- Git

---

## 🔄 CI/CD Pipeline Stages

### 1️⃣ SCM Checkout
- Clones source code from GitHub repository.

### 2️⃣ Application Build
- Executes `mvn clean package`
- Generates executable JAR file.

### 3️⃣ Docker Image Build
- Builds Docker image using Dockerfile.
- Tags image using Jenkins BUILD_NUMBER.

### 4️⃣ DockerHub Login
- Uses Jenkins credentials (dockerlogin).
- Secure authentication using password-stdin.

### 5️⃣ Push to DockerHub
- Pushes tagged image to DockerHub registry.

### 6️⃣ Deploy to Kubernetes
- SSH into Kubernetes master node.
- Executes `kubectl apply -f kubedeploy.yaml`
- Deploys application into cluster.

---

## 📦 Docker Image Repository
DockerHub Image:
ram8243/static-web-app

---

## 📁 Repository Structure
jenkins-cicd-springboot-k8s/
│
├── Jenkinsfile
├── Dockerfile
├── kubedeploy.yaml
├── README.md
|-- Screenshots
|-- commandsused.md

---

## 🎯 Key DevOps Concepts Demonstrated
- CI/CD Automation
- Containerization
- Image Versioning
- Secure Credential Management
- Kubernetes Deployment
- Infrastructure Automation

---

## 🚀 Outcome
Application is automatically:
- Built
- Containerized
- Published to DockerHub
- Deployed to Kubernetes Cluster

Pipeline ensures zero manual deployment effort.
