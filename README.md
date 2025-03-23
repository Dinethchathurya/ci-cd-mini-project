# CI/CD Mini Project: Kubernetes + Tekton + Argo CD

## Overview:
This project automates the process of building a Docker image, pushing it to DockerHub, updating Kubernetes manifests, and deploying to Kubernetes cluster using GitOps (Argo CD).

---

## Folder Structure:
```
ci-cd-mini-project/
├── k8s-manifests/
│   └── deployment.yaml
├── tekton/
│   ├── build-task.yaml
│   ├── build-pipeline.yaml
│   └── pipelinerun.yaml
├── argo/
│   └── application.yaml
```

---

## Prerequisites:

- Kubernetes Cluster (Minikube or any)
- Tekton Pipelines installed
- Argo CD installed
- DockerHub account
- GitHub repo (to host this folder)

---

## Step-by-Step Usage:

### 1️⃣ Setup Argo CD Application:
```bash
kubectl apply -f argo/application.yaml
```

---

### 2️⃣ Apply Tekton Task & Pipeline:
```bash
kubectl apply -f tekton/build-task.yaml
kubectl apply -f tekton/build-pipeline.yaml
kubectl apply -f tekton/pipelinerun.yaml
```

---

### 3️⃣ Watch Pipeline Run:
```bash
kubectl get pipelineruns
kubectl logs <pod-name>
```

---

### 4️⃣ Check Argo CD UI:
- Access Argo CD Dashboard.
- App will sync automatically after pipeline updates manifests.

---

## What to Modify:

- Replace **YOUR_DOCKERHUB_USERNAME** with your DockerHub username.
- Replace **YOUR_GITHUB_USERNAME** and repo URL with your GitHub details.

---

## Full Flow:

1. Push code → Tekton builds Docker image → Push to DockerHub.
2. Tekton updates `deployment.yaml` image tag → pushes to GitHub.
3. Argo CD detects change → auto-syncs and deploys app.

---
