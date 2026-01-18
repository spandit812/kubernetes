
1. Lets say your service is running on port 80 and you want to forward this port to another port (1800).
2. When someone tried to request with port 1800 it will forward the request to port 80.

   ```bash
   kubectl create deployment httpdtest --image=docker.io/httpd
   kubectl expose deployment httpdtest --port=80
   kubectl port-forward svc/httpdtest 1800:80
   ```
   <img width="410" height="112" alt="image" src="https://github.com/user-attachments/assets/be90a879-0d93-495d-a8fd-277259368a85" />

   when you hit http://localhost:1800 it will work.
   This is used for testing purpose.
