# Helm Argocd

### Jenkins Setup
```bash
helm repo add jenkins https://charts.jenkins.io
helm repo update
helm repo ls
helm search repo jenkins
helm search repo jenkins/jenkins --versions
helm show values jenkins/jenkins --version 4.3.20
mkdir -p jenkins/values
helm show values jenkins/jenkins --version 4.3.20 > jenkins/values/jenkins.yaml
helm upgrade --install jenkins --namespace jenkins --create-namespace jenkins/jenkins --version 4.3.20 -f jenkins/values/jenkins.yaml --wait


# Set up port forwarding to the Jenkins UI from Cloud Shell
kubectl -n jenkins port-forward svc/jenkins --address 0.0.0.0 8090:8080

# Jenkins Secrets

kubectl get secrets -n jenkins 

kubectl get secrets/jenkins -n jenkins -o yaml

jenkins-admin-password: b1NuY1NpWmdnR25ZemtuNWx5Mnl0NQ==
jenkins-admin-user: YWRtaW4=

echo -n 'b1NuY1NpWmdnR25ZemtuNWx5Mnl0NQ==' | base64 -d
oSncSiZggGnYzkn5ly2yt5
```

### Argocd Setup

- Helm argocd chart

```bash
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update
helm repo ls
helm search repo argocd
helm search repo argo/argo-cd -l
helm show values argo/argo-cd --version 3.35.4
mkdir -p argocd/values
helm show values argo/argo-cd --version 3.35.4 > argocd/values/argocd.yaml
helm install argocd -n argocd --create-namespace argo/argo-cd --version 3.35.4 -f argocd/values/argocd.yaml
helm upgrade --install argocd -n argocd --create-namespace argo/argo-cd --version 5.51.4 --wait
```
- Helm Image Updater

```bash
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update
helm repo ls
helm search repo argocd
helm search repo argo/argocd-image-updater -l
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
