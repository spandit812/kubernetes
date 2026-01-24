
kubectl get nodes --kubeconfig=...  

--kubeconfig is a GLOBAL flag, not a command-specific flag.  

kubectl commands have two layers of flags:   
1️⃣ Global flags (apply to ALL commands)  
These come before or after the subcommand.  
Examples:  
--kubeconfig  
--context  
--namespace  
--user  
--cluster  
2️⃣ Command-specific flags  
Shown in:  
kubectl get nodes --help  
Examples:  
-o wide  
--show-labels  

🔑 Precedence order (important for exams & debugging)  
Kubectl chooses kubeconfig in this order:  
1️⃣ --kubeconfig flag  
2️⃣ KUBECONFIG env variable  
3️⃣ ~/.kube/config (default)  

kubectl options | grep kubeconfig  
🎯 Pro tip (clean workflow)  
Instead of typing --kubeconfig every time:  
export KUBECONFIG=/path/to/config  
Then just:  
kubectl get nodes  
