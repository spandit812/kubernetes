
---
To quickly deploy the pod and expose to the service
```bash
## Set variable
DEPLOYMENT_NAME=myhttpd

kubectl create deployment $DEPLOYMENT_NAME --image=docker.io/library/httpd
kubectl expose deployment $DEPLOYMENT_NAME --port 8082 --target-port 80
sleep 2
curl $(kubectl get services | grep $DEPLOYMENT_NAME | awk '{print $3}'):8082
```
---
