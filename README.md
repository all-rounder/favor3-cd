# Tech Stack

- Kustomize, ArgoCD

```
eksctl create cluster --name favor3-dev-cluster --region ap-southeast-2 --spot --instance-types=t3.medium --nodes-max=3 --node-volume-size=20
```

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# retrieve admin's password
argocd admin initial-password -n argocd

# port forward 443 for https, 80 for http
kubectl port-forward svc/argocd-server -n argocd 8080:443

kubectl port-forward svc/argocd-server -n argocd 8080:80

# login ArgoCD CLI
argocd login localhost:8080

# Put username and password in one line.
# GitBash has some input problems with some tools, eg. password, yes/no
argocd login localhost:8080 --username admin --password <your-password>
argocd login localhost:8080 --username admin --password <your-password> --insecure

```
