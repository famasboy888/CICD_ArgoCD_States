# CICD ArgoCD Repository

<i>Note: This is the CD part. The CI part is located in [GitHub Actions](https://github.com/famasboy888/CICD_GitAction_ArgoCD_Kubernetes)</i>

## YAML changes will be pushed to ArgoCD repo in GitHub.

<p align="left">
  <img width="80%" height="80%" src="https://github.com/famasboy888/CICD_GitAction_ArgoCD_Kubernetes/assets/23441168/16d8a777-33d8-4dc6-a17d-99c1a1bbf6b2">
</p>

## ArgoCD will sync and re-redeploy new changes.

<p align="left">
  <img width="80%" height="80%" src="https://github.com/famasboy888/CICD_GitAction_ArgoCD_Kubernetes/assets/23441168/8012151c-51c4-47de-9f11-076cb822db77">
</p>


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
kubectl port-forward service/argocd-server -n argocd 8000:443 --address='0.0.0.0'
```

Default username: admin

```bash
#Pass
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

