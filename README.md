# weatherapp Helm Chart

This repository contains a Helm chart for deploying my **weatherapp** on a Kubernetes cluster using **ArgoCD** for GitOps.

## 🚀 Overview

- Helm chart directory: `weatherapp-github-helm/`
- Designed to work with **ArgoCD** for continuous deployment.
- Application containers are pulled from Docker Hub, requiring a Kubernetes image pull secret.

## 🔷 Prerequisites

✅ Kubernetes cluster (v1.21+)  
✅ Helm 3.x (optional, for local testing)  
✅ ArgoCD configured and running in your cluster  
✅ A pre-created Kubernetes secret named `dockerhub-secret` in the target namespace, containing your Docker Hub credentials.
