# Install ArgoCD Server
## Create Kubernetes Namespace for ArgoCD
kubectl create namespace argocd

## Check ArgoCD namespace is created
kubectl get ns

## ArgoCD Releases
https://github.com/argoproj/argo-cd/releases

## Install Latest Version of ArgoCD - NonHA
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

## Install v2.4.0 of ArgoCD - Non-HA
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.4.0/manifests/install.yaml

## Install v2.4.0 of ArgoCD - HA
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.4.0/manifests/ha/install.yaml

## Check ArgoCD Deployments
kubectl get all -n argocd

# Get Default Admin Secret
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

# Access The Argo CD API Server
By default, the Argo CD API server is not exposed with an external IP. To access the API server
## Option-1: Load Balancer Service Type
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'

## Option-2: Port Forwarding
kubectl port-forward svc/argocd-server -n argocd 8080:443

## Option-3: Ingress
How to configure ArgoCD with Ingress https://argo-cd.readthedocs.io/en/stable/operator-manual/ingress/

- Access ArgoCD API Server: http://localhost:8080 or http://<load-balancer-ip>:8080
- Post login change default admin password

# Delete Default Admin Credential
kubectl -n argocd delete secret argocd-initial-admin-secret



