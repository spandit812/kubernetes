---
Deployment is the kind/object/logic which creates pod in the backend.

In the service, if you have created pod and want to change the image or configuration, you will have to do manually one by one for each pod.

in deployment, it maintains the number of pods alive.

deployment can be created by CLI and YML.

CLI:

> kubectl create deployment mydeployment --image=docker.io/httpd
>
> kubectl get deployments
> 
> kubectl scale deployment mydeployment --replica=2
>
> kubectl delete deployment mydeployment
> 
> <img width="329" height="106" alt="image" src="https://github.com/user-attachments/assets/1a148eb9-feb5-4a98-ac04-fb7e406e96f4" />

Once you delete the pod, deployment immediately creates deleted pod.
