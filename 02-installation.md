
---
**IMPORTANT**

If your kubernets version (**kubectl version**) is greate than **>=v1.24**, you do **not need to install docker** in your machine.

Docker is not required on Kubernetes servers because Kubernetes uses CRI-compatible runtimes like containerd. Docker support was removed after Kubernetes v1.24.
> kubectl version

Client Version: v1.34.1

Kustomize Version: v5.7.1

Server Version: v1.34.0
> kubectl version --client=true -o='json'
> 
> kubect get nodes -o wide
> <img width="1181" height="101" alt="image" src="https://github.com/user-attachments/assets/d7c080e4-36e2-48c1-bc77-b84795e28070" />

If you look at this runtime it is , containerd, that is why docker is not required to install. it gives CRI compatible runtime.

**CRI**--> Container runtime Interface

kubelet → Docker (directly)

Not tight coupling

---
<pre>
sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
echo "deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
sudo systemctl enable --now kubelet
systemctl status kubelet
kubelet --version
kubeadm version
kubectl version --client
</pre>
