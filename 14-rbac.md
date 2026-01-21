
1. Go to the folder .kube.
   ```bash
   cd .kube/
   cat config
   ```
   Changing in this file is not recommended.
   
   kind: Config  
   users:  
   <img width="394" height="127" alt="image" src="https://github.com/user-attachments/assets/a9c5a4ff-50e2-4444-9c38-ead8c7feeb3e" />

   **Create service account then clusterrolebinding:**
   ```bash
   kubectl create sa myuser1 -n kubernetes-dashboard
   kubectl create clusterrolebinding myuser-cluster-role-binding --clusterrole=view --serviceaccount=kubernetes-dashboard:myuser1
   kubectl get sa -n kubernetes-dashboard
   kubectl get clusterrolebindings -n kubernetes-dashboard | grep myuser
   ```
--- ---
**create role and role binding at custom namespace level, not at cluster level:**

   ```bash
   kubectl create namespace spandit
   kubectl create sa user3 -n spandit
   kubectl create -f role.yml 
   kubectl create -f role-binding.yml
   ```
   **role.yml file**
   ```yml
      apiVersion: rbac.authorization.k8s.io/v1
      kind: Role
      metadata:
        namespace: spandit
        name: user3-role
      rules:
      - apiGroups: [""] # "" indicates the core API group
        resources: ["deployments","pods"]
        verbs: ["get", "watch", "list"]   
   ```
   **role-binding.yml**
   ```yml
      apiVersion: rbac.authorization.k8s.io/v1
      # This role binding allows "jane" to read pods in the "default" namespace.
      # You need to already have a Role named "pod-reader" in that namespace.
      kind: RoleBinding
      metadata:
        name: read-pods
        namespace: spandit
      subjects:
      # You can specify more than one "subject"
      - kind: ServiceAccount
        name: user3 # "name" is case sensitive
        namespace: spandit
        apiGroup: ""
      roleRef:
        # "roleRef" specifies the binding to a Role / ClusterRole
        kind: Role #this must be Role or ClusterRole
        name: user3-role # this must match the name of the Role or ClusterRole you wish to bind to
        apiGroup: ""
   ```   
