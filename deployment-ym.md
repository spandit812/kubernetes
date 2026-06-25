Create deployment.yml file
```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx-app
    env: dev
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx-pod
  template:
    metadata:
      labels:
        app: nginx-pod
    spec:
      containers:
      - name: nginx-container
        image: nginx
```
It creates Deployment, Replicaset, pods
```bash
kubectl apply -f deployment.yml
```
