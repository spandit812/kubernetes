
---
**To make ane of the node clent machine to do the master job**

Let say if you have one master and 2 nodes running, and you login to the master to run kubectl command is not recommended.  
To keep it secure need to create kubectl client which hits your master.  

<img width="422" height="234" alt="image" src="https://github.com/user-attachments/assets/1747e07e-eb16-4b6e-80f9-eb0674cf2bc9" />

at the master node:
```bash
cat .kube/config
```
copy the content  
```bash
ssh node-ip
vi myconfig
paste the copied content
kubectl get nodes
```
your node will start triggering the command to the master node. So, it is doing the job of master.

---

Above logic is also not secure logic. To make the master node secure from the client flow would be like:

**User-->Assigned to namespace---> Give certain access to the user**
spandit-->namespace-->with some particular access control

1. In kubernetes users are nothing but SSL certificates.
2. Assig role to the ssl
3. Copy that ssl to the client.

```bash
kubectl create ns learning
mkdir createsslcertificate
cd createsslcertificate/
sudo openssl genrsa -out user3.key 2048 # creates private key
sudo openssl req -new -key user3.key -out user3.csr # creates csr certificiate
# Organization name will be namespace name
# Common name wil be user name (certificate name) that is user3.
sudo openssl x509 -req -in user3.csr -CA /etc/kubernetes/pki/ca.crt -CAkey /etc/kubernetes/pki/ca.key -CAcreateserial -out user3.crt -days 500 #signed the certificate
```
