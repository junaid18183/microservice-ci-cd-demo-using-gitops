# Install the ArgoCD

you can simply install the ArgoCD using below command
```
    kustomize build deploy_argo_cd | kubectl apply -f -
```

Make sure to update the ingress created by above and change it with your LoadBalancer IP. Or the real domain instead of `nip.io`


# Access the ArgoCD UI

get the ingress URL for the ArgoCD
```
kubectl get ing -n argocd argocd-server
NAME            CLASS    HOSTS                         ADDRESS         PORTS   AGE
argocd-server   <none>   argocd.192.168.0.108.nip.io   192.168.0.108   80      20m
```

Access the URL argocd.192.168.0.108.nip.io in your Browser.

To get the `admin` password you can use below command

```
kubectl get secret -n argocd argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 --decode
fZQPYPw493j39ke1
```

# Create the ArgoCD Application