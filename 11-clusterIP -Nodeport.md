
1. By default service `type` is CluserIP  
   <img width="438" height="154" alt="image" src="https://github.com/user-attachments/assets/161f374e-e6f4-47b2-b790-94c37c65b194" />

2. NodePort allocates common port on every node
3. 
<img width="411" height="200" alt="image" src="https://github.com/user-attachments/assets/f9c1658d-4102-46cd-8b05-f5c699ed116b" />

4. Exlanation:
     1. When you hit the IP:port (IP with port of any of the node)
     2. It takes you to the service
     3. Service sends the request to the container port

```bash
DEPLOYMENT_NAME=myhttpd7
kubectl create deployment $DEPLOYMENT_NAME --image=docker.io/library/httpd
kubectl expose deployment $DEPLOYMENT_NAME --port 8082 --target-port 80 --type NodePort
kubectl get svc
```
<img width="484" height="175" alt="image" src="https://github.com/user-attachments/assets/fa9a094e-84fc-4aba-8d5e-4985fc83f202" />
