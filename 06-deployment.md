---
Deployment is the kind/object/logic which creates pod in the backend.

In the service, if you have created pod and want to change the image or configuration, you will have to do manually one by one for each pod.

in deployment, it maintains the number of pods alive.

deployment can be created by CLI and YML.

CLI:

> kubectl create deployment mydeployment --image=docker.io/httpd
