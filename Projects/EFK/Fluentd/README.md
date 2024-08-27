In this lab, we'll explore how to deploy Fluentd on Kubernetes as a DaemonSet. This ensures that a Fluentd instance runs on every node, enabling efficient log collection from both the nodes and the pods. 
To deploy fluentd in a kubernetes cluster we should: 

- **ensure that the cluster is up and running**

- **deploy fluentd as a daemonset, this ensures that a copy of the pod runs on each node in the cluster. This is perfect for log collection, as we want Fluentd to collect logs from every node.**
- **Create a Fluentd Configuration File**


