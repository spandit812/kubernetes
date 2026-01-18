
Namespace:
1. Namespace is used to isolate the things logically.
   

```bash
kubectl get ns # ns is used for namespace
kubectl create namespace tcs
kubectl create deployment --image=docker.io/httpd -n tcs # this deployment will be done under namespace tcs
kubectl get pods -n tcs
kubectl get deployment -n tcs
```

Get system pods:

```bash
 kubectl get pods -n kube-system
```
