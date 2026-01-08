
Service is a kind, object which does load balancing in kubernetes.

It is the object which groups the pod together

---
How will service map to the pod?

Every pod will have lable and that label will be passed in the server for mapping.

In service, label will be passed in the **selector**

1. pod1
<pre>
vi pod1.yml
apiVersion: v1
kind: Pod
metadata:
  name: httpd-pod1
  labels:
    mycka: spanditlearn
spec:
  containers:
  - name: httpd-container-1
    image: httpd
    ports:
    - containerPort: 80
</pre>

2. pod2

<pre>
vi pod2.yml
apiVersion: v1
kind: Pod
metadata:
  name: httpd-pod2
  labels:
    mycka: spanditlearn
spec:
  containers:
  - name: httpd-container-2
    image: httpd
    ports:
    - containerPort: 80
</pre>

> kubectl create -f pod1.yml
> 
> kubectl create -f pod2.yml
>
> kubectl get pods --show-labels
>
<pre>
vi service.yml
  
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    mycka: spanditlearn
  ports:
    - protocol: TCP
      port: 8085
      targetPort: 80
</pre>

> kubectl create -f service.yml
> 
> kubectl get svc
> 
> curl ip:8085
