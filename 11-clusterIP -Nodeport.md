
1. By default service `type` is CluserIP  
2. NodePort allocates common port on every node
3. 
<img width="411" height="200" alt="image" src="https://github.com/user-attachments/assets/f9c1658d-4102-46cd-8b05-f5c699ed116b" />

4. Exlanation:
     1. When you hit the IP:port (IP with port of any of the node)
     2. It takes you to the service
     3. Service sends the request to the container port

