
<pre>
<img width="370" height="124" alt="image" src="https://github.com/user-attachments/assets/4c8730ff-1973-4c42-842a-b41c07cadba3" /><img width="370" height="124" alt="image" src="https://github.com/user-attachments/assets/8d3b6e58-4d2d-4d0e-a27d-5efab4120be9" />

</pre>
---
On the master machines these components are there:

  **APIServer-->** takes all request from the end user (administrator) by any of the input type like: API, CLI, UI ---> The talks to **kubelet** and 
  all authentication and authorization part. It's kind of front page/reception of the office
  Diagram is also called **3+1 diagram**
  
  **etcd-->** It is a dataase of cluster which maintainer the nodes detail. It is key value paire which holds all the details of nodes, how many pods are running...

  **Scheduler-->** It checks the configuration, which cpu has high memory available, and selects / election of the node. Then it passes the request to controller.

  **Controller-->** Controller will talk to Kubelet and Kubelet will talk to docker, so that container will get created.
