

> kubectl create deployment mydep2 --replicas=2 --image=docker.io/library/nginx
> 
> kubectl get deployments
> 
> kubectl expose deployment mydep2 --port=**80**
> 
> kubectl get services
>
> kubectl get pods --show-labels
>
> sleep 2  # Adding delay for 2 seconds to be service stable 
> 
> kubectl describe service mydep2 | grep IP: | awk '{print $2}'
>
> sleep 2 # Adding delay for 2 seconds to be service stable
> 
> curl $(kubectl describe service mydep2 | grep IP: | awk '{print $2}'):**80**
> 
