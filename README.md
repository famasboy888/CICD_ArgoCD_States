# CICD ArgoCD Repository

This is the repository storing all state files for ArgoCD in my Kubernetes Cluster 

## Installation

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## Viewing of pods, deployments and services

```bash
kubectl get all -n argocd
```

## Accessing Dashboard

Note: I got stuck coz we need to add flag `--address='0.0.0.0'` to allow all traffic.

```bash
kubectl port-forward service/argocd-server -n argocd 8080:443 --address='0.0.0.0'
```

Default username: admin

```bash
#Pass
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

