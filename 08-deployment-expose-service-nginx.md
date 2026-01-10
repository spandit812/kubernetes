
---
**Example-1**

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
---

**Example-2**  Added --target-port= at the time of expose 

> kubectl create deployment mydep3 --replicas=2 --image=docker.io/library/nginx
> 
> kubectl get deployments
> 
> kubectl expose deployment mydep3 --port=**81** **--target-port=80**
> 
> kubectl get services
>
> kubectl get pods --show-labels
>
> sleep 2  # Adding delay for 2 seconds to be service stable 
> 
> kubectl describe service mydep3 | grep IP: | awk '{print $2}'
>
> sleep 2 # Adding delay for 2 seconds to be service stable
> 
> curl $(kubectl describe service mydep3 | grep IP: | awk '{print $2}'):**81**
