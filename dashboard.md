
Now, kubernetes dashboard is created using helm. Still we can use old manifest to create dashboard.

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
kubect get pods -n kubernetes-dashboard
kubect get svc -n kubernetes-dashboard
kubectl delete clusterrolebinding kubernetes-dashboard
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=admin --serviceaccount=kubernetes-dashboard:kubernetes-dashboard
kubectl get sa -n kubernetes-dashboard  # sa is service account which is user, refer in 14-rbac.md file
```
