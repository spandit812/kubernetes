
---
Create a simple pod

https://kubernetes.io/docs/concepts/workloads/pods/

tee pod.yml 0<<EOF
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
> kubectl create -f pod.yml
>
> kubectl get pods -o widd
> 
> Here -f stands for file.
