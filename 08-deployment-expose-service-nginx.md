

> kubectl create deployment mydep2 --replicas=2 --image=docker.io/library/nginx
> 
> kubectl get deployments
> 
> kubectl expose deployment mydep2 --port=**80**
> 
> kubectl get services
> 
> kubectl describe service mydep2 | grep IP: | awk '{print $2}'
> 
> curl $(kubectl describe service mydep2 | grep IP: | awk '{print $2}'):**80**
> 
