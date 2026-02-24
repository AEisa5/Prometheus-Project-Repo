# 🚀 Node.js Application Deployment with Kubernetes, Prometheus & Grafana

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-18+-green" />
  <img src="https://img.shields.io/badge/Docker-Containerized-blue" />
  <img src="https://img.shields.io/badge/Kubernetes-Orchestrated-326CE5" />
  <img src="https://img.shields.io/badge/Monitoring-Prometheus-orange" />
  <img src="https://img.shields.io/badge/Visualization-Grafana-F46800" />
</p>

---

## 📌 Project Overview

This project demonstrates a complete **cloud-native deployment pipeline** for a Node.js application including:

* ✅ Containerization using Docker
* ✅ Image publishing to Docker Hub
* ✅ Deployment on Kubernetes (kubeadm cluster)
* ✅ Metrics collection with Prometheus
* ✅ Visualization with Grafana
* ✅ Alerting using Alertmanager

The architecture follows modern DevOps and Observability best practices used in real production environments.

---

# 🏗 Architecture Diagram

![Architecture Diagram](Screenshots/Screenshot%202026-02-23%20112318.png)

![Architecture Diagram](Screenshots/Screenshot%202026-02-23%20112402.png)


---

# 🧠 Architecture Explanation

The system is divided into two main layers:

## 1️⃣ Build & Containerization Layer

**Components:**

* Node.js Application
* Dockerfile
* Docker Image
* Docker Hub Registry

### Flow

1. Build Docker image from the Dockerfile.
2. Push the image to Docker Hub.
3. Kubernetes pulls the image during deployment.

---

## 2️⃣ Kubernetes & Monitoring Layer

Inside the Kubernetes Cluster:

* **Deployment** → Manages Node.js Pods
* **Service (ClusterIP)** → Exposes the application internally
* **Prometheus** → Scrapes application metrics
* **Alertmanager** → Handles alert notifications
* **Grafana** → Visualizes metrics using dashboards

---

# 🔄 Monitoring & Data Flow

### Application Monitoring Flow

1. Node.js application exposes `/metrics` endpoint.
2. Prometheus scrapes metrics periodically.
3. Prometheus evaluates alert rules.
4. Alertmanager sends notifications (e.g., Slack).
5. Grafana visualizes collected metrics.

```
Node App → Prometheus → Grafana
```

Prometheus uses a **Pull Model**, which is ideal for Kubernetes-based environments.

---

# 📂 Project Structure

```
.
├── Dockerfile
├── app.js
├── package.json
├── k8s/
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── prometheus.yaml
│   ├── alertmanager.yaml
│   └── grafana.yaml
└── Screenshot/
    └── Screenshot%202026-02-23%20112402.png
```

---

# 🐳 Docker Setup

## 🔹 Build Image

```bash
docker build -t <your-dockerhub-username>/node-app:v1 .
```

## 🔹 Push Image

```bash
docker login
docker push <your-dockerhub-username>/node-app:v1
```

---

# ☸ Kubernetes Deployment

Apply all manifests:

```bash
kubectl apply -f k8s/
```

Verify resources:

```bash
kubectl get pods
kubectl get svc
```

---

# 📊 Prometheus Configuration

Prometheus scrapes metrics from:

```
http://nodejs-svc:3000/metrics
```

Ensure your Node.js app exposes metrics using:

```bash
npm install prom-client
```

---

# 📈 Grafana Setup

1. Expose Grafana service (NodePort or Ingress).
2. Access Grafana UI.
3. Add Prometheus as a data source.
4. Import or create dashboards.

---

# 🔔 Alerting Configuration

Prometheus alert rules trigger notifications when:

* 🚨 CPU usage exceeds threshold
* 🚨 Memory usage exceeds threshold
* 🚨 Pod crashes
* 🚨 HTTP error rate increases

Alertmanager forwards alerts to configured channels (e.g., Slack).

---

# 🧪 Example Use Cases

* Monitor API response time
* Track container resource consumption
* Detect service downtime
* Visualize traffic patterns

---

# 🎯 Skills Demonstrated

* Docker & Containerization
* Kubernetes Deployments & Services
* Infrastructure Monitoring
* Observability & Metrics
* Alerting & Incident Response
* DevOps Best Practices

---

# 🚀 Future Improvements

* 🔄 Horizontal Pod Autoscaler (HPA)
* 🌐 Ingress Controller with TLS
* 🔁 CI/CD Pipeline Integration
* 📦 Helm Chart Packaging

---

# 👨‍💻 Author

**Ahmed Essa**
DevOps & Cloud Enthusiast

---

⭐ If you found this project useful, consider giving it a star!
