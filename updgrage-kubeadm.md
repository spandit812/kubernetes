```bash
sudo apt update -y
sudo apt-cache madison kubeadm
kubectl get nodes

sudo apt-mark unhold kubeadm && \
sudo apt-get update && sudo apt-get install -y kubeadm=1.23.5-00 && \
sudo apt-mark hold kubeadm

sudo kubeadm upgrade plan
sudo kubeadm upgrade apply v1.23.5

sudo apt-mark unhold kubelet kubectl && \
sudo apt-get update && sudo apt-get install -y kubelet=1.23.5-00 kubectl=1.23.5-00 && \
sudo apt-mark hold kubelet kubectl

kubectl get nodes
```
