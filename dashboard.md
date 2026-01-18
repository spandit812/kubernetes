
Now, kubernetes dashboard is created using helm. Still we can use old manifest to create dashboard.

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
kubect get pods -n kubernetes-dashboard
kubect get svc -n kubernetes-dashboard
```
