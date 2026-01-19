````md
# Kubernetes Deployment – Tic Tac Toe (GitOps Ready)

This directory contains **Kubernetes manifests** for deploying the Tic Tac Toe application using **GitOps principles** as part of a **DevSecOps pipeline**.

The manifests can be:
- Applied manually using `kubectl` (local/testing)
- Continuously synced by **Argo CD** (recommended)

---

## Components

1. **Deployment** – Manages application pods, rolling updates, and scaling  
2. **Service** – Exposes the application within the cluster  
3. **Ingress** – Exposes the application to external traffic  

---

## Prerequisites

- Kubernetes cluster (Minikube, EKS, GKE, AKS, etc.)
- `kubectl` configured to communicate with the cluster
- Ingress controller installed (e.g., NGINX Ingress)
- Container registry access (GitHub Container Registry – GHCR)

---

## Setup Container Registry Secret (GHCR)

Create a Kubernetes secret to pull images from **GitHub Container Registry**:

```bash
kubectl create secret docker-registry ghcr-secret \
  --docker-server=ghcr.io \
  --docker-username=YOUR_GITHUB_USERNAME \
  --docker-password=YOUR_GITHUB_TOKEN \
  --docker-email=YOUR_EMAIL
````

> The GitHub token must have `read:packages` permission.

Reference this secret in the `Deployment` using `imagePullSecrets`.

---

## Deployment Options

### Manual Deployment (Optional)

```bash
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
kubectl apply -f kubernetes/ingress.yaml
```

Verify:

```bash
kubectl get pods
kubectl get services
kubectl get ingress
```

---

### GitOps Deployment (Recommended)

In a **GitOps workflow**:

1. CI builds and pushes a new container image
2. CI updates the image tag in `deployment.yaml`
3. Changes are committed to Git
4. **Argo CD** automatically syncs the manifests to Kubernetes

> No manual `kubectl apply` is required in this mode.

---

## Accessing the Application

### Minikube

```bash
minikube service tic-tac-toe --url
```

### Ingress

If an Ingress is configured with a domain:

```text
http://tic-tac-toe.example.com
```

---

## Scaling

Scale the application manually:

```bash
kubectl scale deployment tic-tac-toe --replicas=5
```

---

## Updating the Application

### Manual Rollout

```bash
kubectl rollout restart deployment tic-tac-toe
```

### GitOps Rollout (Preferred)

* Update the image tag in Git
* Commit and push
* Argo CD handles the rollout automatically

---

## Monitoring & Troubleshooting

Check resource status:

```bash
kubectl get deployments
kubectl get pods
kubectl get services
kubectl get ingress
```

View logs:

```bash
kubectl logs -l app=tic-tac-toe
```

---

## Notes

* Kubernetes manifests are the **single source of truth**
* CI pipelines should not deploy directly to production
* Argo CD ensures the cluster state always matches Git

```

---

If you want, next I can **update `deployment.yaml` itself** (add probes, resource limits, security best practices) so this README and manifests **perfectly match** and look production-grade.
```
