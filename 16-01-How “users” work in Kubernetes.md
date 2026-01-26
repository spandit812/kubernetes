**1️⃣ First: How “users” work in Kubernetes (important concept)**  

There is nothing like user to create  
❌ No kubectl create user  
✅ Kubernetes trusts credentials (certs, tokens, OIDC, etc.)  

**RBAC is only about authorization, not authentication**  

**2️⃣ Goal (what we’ll build)** 

We will:  
1. Create a namespace: dev
2. Create a user: dev-user
3. Give dev-user limited permissions in dev namespace
4. Add this user to ~/.kube/config
5. Switch context and test permissions

**Create Namespace:**  
```bash
kubectl create namespace dev
kubect get ns
```
**Create User(Certificates is user in kubernetes):**  
```bash
openssl genrsa -out dev-user.key 2048
openssl req -new -key dev-user.key -out dev-user.csr -subj "/CN=dev-user"
# CN must match the user-name that is dev-user
openssl x509 -req -in dev-user.csr   -CA /etc/kubernetes/pki/ca.crt   -CAkey /etc/kubernetes/pki/ca.key   -CAcreateserial   -out dev-user.crt   -days 365
```
**Create Role:**  
```bash
tee role.yaml 0<<EOF
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: dev-role
  namespace: dev
rules:
- apiGroups: [""]
  resources: ["pods", "services"]
  verbs: ["get", "list", "create", "delete"]
EOF

kubectl create -f role.yaml
```
**Create RoleBinding:**
```bash
tee rolebinding.yaml 0<<EOF
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: dev-rolebinding
  namespace: dev
subjects:
- kind: User
  name: dev-user
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: dev-role
  apiGroup: rbac.authorization.k8s.io
EOF

kubectl create -f rolebinding.yaml
```
**Set Credentials and context and set for the current user:**  
```bash
kubectl config set-credentials dev-user --client-certificate=dev-user.crt --client-key=dev-user.key
kubectl config set-context dev-user-context --cluster=$(kubectl config view --minify -o jsonpath='{.clusters[0].name}') --namespace=dev --user=dev-user
kubectl config use-context dev-user-context
kubectl config current-context

kubectl get pods
kubectl create deployment nginx --image=nginx
```
**Go back to admin context:** 
```bash
kubectl config get-contexts 
kubectl config use-context <admin-context-name>
```









