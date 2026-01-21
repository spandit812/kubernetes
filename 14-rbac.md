
1. Go to the folder .kube.
   ```bash
   cd .kube/
   cat config
   ```
   Changing in this file is not recommended.
   
   kind: Config  
   users:  
   <img width="394" height="127" alt="image" src="https://github.com/user-attachments/assets/a9c5a4ff-50e2-4444-9c38-ead8c7feeb3e" />

   Create service account:
   ```bash
   kubectl create sa myuser1 -n kubernetes-dashboard
   kubectl create clusterrolebinding myuser-cluster-role-binding --clusterrole=view --serviceaccount=kubernetes-dashboard:myuser1
   kubectl get sa -n kubernetes-dashboard
   kubectl get clusterrolebindings -n kubernetes-dashboard | grep myuser
   ```
