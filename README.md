# argoCD

#### Note: this should be done on an already running K8s cluster
#### Install argo using the install.yaml file provided
```
  kubectl -n argocd apply -f Install.yaml
```

#### Get access to monitor your kubernetes cluster and how argocd does the changes
```
  kubectl port-forward svc/argocd-server -m argocd 8080:443
```

#### Argocd gets the polling of the state of deployment files and makes changes to the K8s cluster as changes are made to the application deployment file.

#### Jenkins can be used to handle CI by doing SCM polling for changes in the repo that contains the application files in the other repository provided and trigger the pipeline for changes. It can also create a new application image for major changes made.
Get character from stdin. Returns the next character from the standard input (stdin)
