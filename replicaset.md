```bash
kubectl api-resources | grep -iE 'kind|replica'
```
<img width="852" height="88" alt="image" src="https://github.com/user-attachments/assets/fb26e8c0-53a1-4b39-a214-3f185a48ad60" />  

Here this **SHORTNAMES** from the screeshot shows that instead of using **replicaset** in the command we can use **rs**  
example:   

```bash
kubectl get replicaset
```
OR  
```bash
kubectl get rs
```

1. YML file to create replica set with 3 replias
2. 
   **MatchLabels must match with the metadata labels in the below yml file**  
   ```bash
   matchLabels:
      app: nginx-pod
   ```
   ```bash
   template:
    metadata:
      labels:
        app: nginx-pod
   ```
3. Save this replicaset.yml
   
```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-replicaset
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
4. kubectl apply -f replicaset.yml  
5. Here Desired state and Current state number of pods count will always be same and maintained by replica set.   
<img width="400" height="75" alt="image" src="https://github.com/user-attachments/assets/b684d035-727b-49a6-b3b4-17f5f4067b2a" />  
6. There are the pods
   <img width="807" height="117" alt="image" src="https://github.com/user-attachments/assets/2e29f6f8-694b-4afa-84d6-d9f565a06638" />  
   
7. **Delete All the resources created by replicaset.yml**  
   ```bash
   kubectl delete -f replicaset.yml  
   ```

