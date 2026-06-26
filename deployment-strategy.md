Here I will be discussing about deployment strategy: **RollingUpdate**  
```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx-pod
  template:
    metadata:
      name: nginx-pod
      labels:
        app:nginx-pod
    spec:
    - name: nginx-container
      image: ngin
```

