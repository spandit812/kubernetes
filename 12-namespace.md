
Namespace:
1. Namespace is used to isolate the things logically.
   

```bash
kubectl get ns # ns is used for namespace
kubectl create namespace tcs
kubectl create deployment --image=docker.io/httpd -n tcs # this deployment will be done under namespace tcs
kubectl get pods -n tcs
kubectl get deployment -n tcs
```

**Get system pods:**

```bash
 kubectl get pods -n kube-system
```
**To set the default namespace to tcs**, **Changed back to default**

```bash
kubectl config set-context --current --namespace=tcs # now if you see .kube/config it will have tcs namespace set
kubectl get pods# now it will give you the pods from tcs namespace only.
kubectl config set-context --current --namespace=default # to set the namespace to default.
```
