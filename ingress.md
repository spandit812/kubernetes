**Step 1 — Install Ingress Controller**  

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
```

--------  
IMPORTANT

This creates MANY resources:
---
Resource	Purpose  
Namespace	ingress-nginx  
ServiceAccount	API identity  
ClusterRole	Permissions  
ClusterRoleBinding	Attach permissions  
Deployment	Controller pods  
Service	Expose controller  

---
Verify Pods
---  
```
kubectl get pods -n ingress-nginx
```
Wait until:
---
Running  

---
Step 2 — Create Application  
Create nginx deployment.  
---
```
kubectl create deployment mynginx --image=nginx
```
---
Verify
---
```
kubectl get pods
```
---
Step 3 — Create Service
---
Expose deployment internally.  

```
kubectl expose deployment mynginx \
  --port=30001 \
  --target-port=80 \
  --type=ClusterIP
```
---
IMPORTANT UNDERSTANDING
---
| Field	        | Meaning  

port=30001	    |  Service Port  
target-port=80	|  nginx container port  
---
---
Verify Service
---
```
kubectl get svc
```
---
Step 4 — Verify Internal Connectivity
---
Create curl pod.
```
kubectl run curl-pod \
  --image=curlimages/curl \
  -- sleep 3600
```
---
Enter Pod
---
```
kubectl exec -it curl-pod -- sh
```

Test Service  
```
curl mynginx:30001  
```
Expected:  

Welcome to nginx!  

---
Step 5 — Create Ingress Resource
---
```yml
apiVersion: networking.k8s.io/v1
kind: Ingress

metadata:
  name: myingress

spec:
  ingressClassName: nginx

  rules:
  - http:
      paths:

      - path: /
        pathType: Prefix

        backend:
          service:
            name: mynginx

            port:
              number: 30001
```
---
MOST IMPORTANT LINE
---
number: 30001  

This must match:  

Service port  
NOT container port.

---
Apply Ingress
---
```
kubectl apply -f ingress.yml
```
---
Verify Ingress
---
```kubectl describe ingress myingress```

Expected:  

Backend:  
  mynginx:30001  

---
Step 6 — Find Ingress Controller Port
---
```
kubectl get svc -n ingress-nginx
```
---
Step 7 — Get Node IP
---
```
kubectl get nodes -o wide
```
---
Step 8 — Access Ingress
---

```
curl http://NODE-IP:NODEPORT
```
---
FINAL FLOW
---

Client  
   |  
Ingress Controller Service  
   |  
Ingress Controller Pod  
   |  
Ingress Rules  
   |  
mynginx Service  
   |  
NGINX Pod  
