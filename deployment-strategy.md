Here I will be discussing about deployment strategy: **RollingUpdate**  

save the yml by name deployment.yml  

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
        image: nginx
```
**--record=true**  this is used to see the revisions for the rollout happend  
```bash
kubectl apply -f deployment.yml --record=true
kubectl rollout history deployment nginx-deployment
kubectl get events
```

