
---
> kubectl create deployment mysqldepl --image=docker.io/library/mysql:9.5.0 --dry-run=client -o yaml > mydb.yml
> vi mydb.yml
>
<pre>
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: mysqldepl
  name: mysqldepl
spec:
  replicas: 1
  selector:
    matchLabels:
      app: mysqldepl
  strategy: {}
  template:
    metadata:
      labels:
        app: mysqldepl
    spec:
      containers:
      - image: docker.io/library/mysql:9.5.0
        name: mysql
        env:
        - name: MYSQL_ROOT_PASSWORD
          value: mypassword
        - name: MYSQL_DATABASE
          value: mydatabase
        resources: {}
status: {}
</pre>

> kubectl create  -f mydb.yml
> 
> kubectl get deployments.apps
> 
> kubectl get pods
>
> <img width="391" height="65" alt="image" src="https://github.com/user-attachments/assets/8023aa83-d78f-47ae-b054-ea35ab146b9a" />

> kubectl exec mysqldepl-6fb6bdc5f4-bkqzf  -it -- bash
> 
> mysql -uroot -pmypassword
>kubectl exec -it mysqldepl-6fb6bdc5f4-bkqzf -c bash
