
---
1. Create a simple pod

https://kubernetes.io/docs/concepts/workloads/pods/
<pre>
tee pod.yml 0 << EOF 
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
</pre>
> kubectl create -f pod.yml
>
> kubectl get pods -o wide
>
> curl ip-address-of-pod
> 
> Here -f stands for file.

2. hello openshift
<pre>
tee pod.yml 0 << EOF
apiVersion: v1
kind: Pod
metadata:
  name: openshift-pod
spec:
  containers:
  - name: openshift-container
    image: openshift/hello-openshift
    ports:
    - containerPort: 8080
> EOF
</pre>
> kubectl create -f pod.yml
> 
>  kubectl get pods -o wide
> 
>  curl ip-address:8080

---
> kubectl get events
> 
> kubectl delete pod openshift-pod
