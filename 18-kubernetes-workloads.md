<img width="679" height="452" alt="image" src="https://github.com/user-attachments/assets/56670db9-5f83-40e3-8dd5-f8bd936ab450" />
Workload is not a single entity. Pod can be defined as workload, similarly, deployment, Service, Job are workloads.
**Job & CronJob**  
Job is one time activity where as CronJob is repeatative activity.  
It runs only once, and create the pod and run it and mark it "Completed"  
```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: pi
spec:
  template:
    spec:
      containers:
      - name: pi
        image: perl:5.34.0
        command: ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
      restartPolicy: Never
  backoffLimit: 4

```
**CronJob**  
```yaml
apiVersion: batch/v1
kind: CronJob
metadata:
  name: hello
spec:
  schedule: "* * * * *"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: hello
            image: busybox:1.28
            imagePullPolicy: IfNotPresent
            command:
            - /bin/sh
            - -c
            - date; echo Hello from the Kubernetes cluster
          restartPolicy: OnFailure
```
**DeamonSet**  
DeamonSet is a pod which runs on every nodes  
To check each node logs.
Whenever we create pods with deployment with replicas, it does not give guarantee to create pods on each node.
It ensures a specific Pod runs on every node (or selected nodes) in the cluster.  
