# Helm Argocd

### Argocd Setup

- Helm argocd chart

```bash
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update
helm repo ls
helm search repo argocd
helm show values argo/argo-cd --version 3.35.4
mkdir -p argocd/values
helm show values argo/argo-cd --version 3.35.4 > argocd/values/argocd.yaml
helm install argocd -n argocd --create-namespace argo/argo-cd --version 3.35.4 -f argocd/values/argocd.yaml
```
- Helm Image Updater

```bash
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update
helm repo ls
helm search repo argocd
helm show values argo/argocd-image-updater --version 0.8.5
mkdir -p argocd/values
helm show values argo/argocd-image-updater --version > argocd/values/argocd-image-updater.yaml
helm upgrade --install argocd-image-updater -n argocd argo/argocd-image-updater --version 0.8.5 -f argocd-image-updater.yaml --wait
```

- Repo Pull & Push Setup in ArgoCD with Access Toekn

```bash
https://gitlab.com/quickbooks2018/kaniko.git
jenkins
glpat-xVz4Xp-14M6dvMMdWYKx
```