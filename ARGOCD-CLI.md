# argocd

# ARGOCD CLI
To install and configure ArgoCD CLI , refer this [link](https://github.com/mykloudjourney/pre-requisites/blob/main/install-argocli.md)

## LOGIN to ARGOCD API SERVER
```shell
$ argocd login localhost:8080 --name minikube --username admin --password argoadmin --insecure
```

# CHANGE ARGOCD SERVER LOGIN PASSWORD
```shell
$ argocd account update-password --account admin --current-password 123 --new-password argoadmin --insecure
```

# VIEW ARGOCD APP STATUS
```shell
$ kubectl get po -n guestbook
```

# SYNC ARGO APP
```shell
$ argocd app sync guestbook
```