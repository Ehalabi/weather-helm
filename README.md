# weatherapp Helm Chart

This repository contains a Helm chart for deploying my **weatherapp** on a Kubernetes cluster using **ArgoCD** for GitOps.

## 🚀 Overview

- Helm chart directory: `weatherapp-github-helm/`
- Designed to work with **ArgoCD** for continuous deployment.
- Application containers are pulled from Docker Hub (or another container registry), requiring a Kubernetes image pull secret if the registry is private.

## 🔷 Prerequisites

✅ Kubernetes cluster (v1.21+)  
✅ Helm 3.x (optional, for local testing)  
✅ ArgoCD configured and running in your cluster  
✅ Docker image for `weather-webapp` built and pushed to your container registry  
✅ (If private) a pre-created Kubernetes secret named `dockerhub-secret` in the target namespace, containing your registry credentials.

## 🔷 Building the Application Image

This chart assumes that the weather web application image has already been built and published.  
You can use the [weather-webapp](https://github.com/Ehalabi/weather-webapp) repository to build and push your own image:

```bash
# Clone the application repository
git clone https://github.com/Ehalabi/weather-webapp
cd weather-webapp

# Build and push the Docker image
docker build -t your-dockerhub-username/weather-webapp .
docker push your-dockerhub-username/weather-webapp
```

Then edit `weatherapp-github-helm/values.yaml` if needed to specify your image repository and tag:
```yaml
image:
  repository: your-dockerhub-username/weather-webapp
  tag: latest
```

If your registry is private, create the secret:
```bash
kubectl create secret docker-registry dockerhub-secret \
  --docker-username=YOUR_USERNAME \
  --docker-password=YOUR_PASSWORD \
  --docker-email=YOUR_EMAIL \
  -n YOUR_NAMESPACE
```

## 🔷 Deployment

Once everything is set up, you can deploy the chart using ArgoCD or Helm.

---
