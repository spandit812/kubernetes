
---

```bash
kubectl create deployment mysql --image=mysql:8  
kubectl edit deployments.apps mysql  
```
**# Inside spec.template.spec.containers, add:**
```yml
ports:
- containerPort: 3306
env:
- name: MYSQL_ROOT_PASSWORD
  value: rootpass
- name: MYSQL_DATABASE
  value: wordpress
```
```bash
kubectl expose deployment mysql --port=3306 --target-port=3306 --name=mysql
kubectl get pods
kubectl get svc
kubectl get endpoints mysql
```

```bash
kubectl create deployment wordpress   --image=wordpress:latest
kubectl edit deployment wordpress
```
```yaml
ports:
- containerPort: 80
env:
- name: WORDPRESS_DB_HOST
  value: mysql
- name: WORDPRESS_DB_USER
  value: root
- name: WORDPRESS_DB_PASSWORD
  value: rootpass
- name: WORDPRESS_DB_NAME
  value: wordpress
```
```bash
kubectl expose deployment wordpress   --type=NodePort   --port=80
kubectl get svc wordpress
curl 172.20.187.113:80
```
