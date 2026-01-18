
1. How to make master node schedulable.
   * kubect edit node master-node-name
   * Remove below lines
     ```yaml
       taints:
       - effect: NoSchedule
         key: node-role.kubernetes.io/control-plane
     ```
     in the pod.yml mention **nodeName:** master-nodename
