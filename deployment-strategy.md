Here I will be discussing about deployment strategy: **RollingUpdate**  

save the yml by name deployment-without-rollout.yml  

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx-app
spec:
  replicas: 5
  selector:
    matchLabels:
      app: nginx-pod
  template:
    metadata:
      name: nginx-pod
      labels:
        app: nginx-pod
    spec:
      containers:
      - name: nginx-container
        image: nginx
```

```bash
kubectl apply -f deployment-without-rollout.yml --record=true
```

**With rollout:**  
save the yma by name deployment-with-rollout.yml  

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx-app
spec:
  replicas: 5
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 25%
      maxSurge: 25%
  selector:
    matchLabels:
      app: nginx-pod
  template:
    metadata:
      name: nginx-pod
      labels:
        app: nginx-pod
    spec:
      containers:
      - name: nginx-container
        image: caddy
```


**--record=true**  this is used to see the revisions for the rollout happend  
```bash
kubectl apply -f deployment-with-rollout.yml --record=true
kubectl rollout status deployment --nginx-deployment
kubectl rollout history deployment nginx-deployment
kubectl get events
```
Once I change the image: caddy and run command
```bash
kubectl rollout history deployment nginx-deployment
```
you will see the revisions  
<img width="556" height="126" alt="image" src="https://github.com/user-attachments/assets/6daf5260-104d-49ea-b968-615746c8bba2" />

=======================================================================   

**In case of rollback the change**  
```bash
kubectl rollout undo deployment nginx-deployment --to-revision=1
```

After rollback I see  
<img width="600" height="177" alt="image" src="https://github.com/user-attachments/assets/6084ed1b-ff7d-43a8-8923-fa27f7fd4104" />
