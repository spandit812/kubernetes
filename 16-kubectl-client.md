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
