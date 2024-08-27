The EFK stack combines Elasticsearch, Fluentd, and Kibana to aggregate, store, and visualize logs from multiple sources within a Kubernetes environment.

Components of the EFK Stack
- Elasticsearch 🔎: A distributed, RESTful search and analytics engine capable of addressing a growing number of use cases.

- Fluentd 🚿: An open-source data collector for unified logging, which allows you to unify data collection and consumption for better use and understanding of data.

- Kibana 📊: A visualization layer that works on top of Elasticsearch, providing a user-friendly interface to visualize data.


Deploying the EFK stack on Kubernetes involves setting up each component to work together seamlessly. There are multiple ways of deploying the stack like manual deployment, helm charts, operators and pre-built cloud marketplace solutions. In this lab, we will follow the manual deployment approach using individual manifest files.

# step 1 : Deploy Elasticsearch 

Elasticsearch - the backend of the EFK stack - is basically a Document-based NoSQL database that runs on port 9200 by default.
Elasticsearch doesn't just store data but also ensures data durability and failure recovery by utilizing replication. To ensure quick availability of data, it utilizes sharding in addition to replication.
In an elasticsearch cluster, its the master node that coordinates actions and manages changes.

Deploying Elasticsearch on Kubernetes involves setting up a StatefulSet for stable pod identification and storage, configuring Persistent Volumes for data persistence, and using Services for stable network access. By following these steps, you can ensure a resilient and scalable Elasticsearch cluster within your Kubernetes environment. This guide aimed to provide a beginner-friendly introduction to deploying Elasticsearch on Kubernetes, covering the essential components and configurations.

# setp 2 : Deploy Fluentd

Fluentd - the log shipper - utilizes a variety of plugins for filtering and transforming log data. These plugins are defined in the fluentd configuration file, which uses the .conf extension.
Fluentd uses memory buffering mechanism to ensure reliable log delivery to Elasticsearch.

In this lab, we'll explore how to deploy Fluentd on Kubernetes as a DaemonSet. This ensures that a Fluentd instance runs on every node, enabling efficient log collection from both the nodes and the pods. 
To deploy fluentd in a kubernetes cluster we should: 

- **ensure that the cluster is up and running**

- **deploy fluentd as a daemonset, this ensures that a copy of the pod runs on each node in the cluster. This is perfect for log collection, as we want Fluentd to collect logs from every node.**
- **Create a Fluentd Configuration File**

# step 3 : Deploy Kibana

Kibana - the visualization wizard - provides extensive data presentation capabilities through graphs and charts and runs on port 5601 by default.

Deploying Kibana involves creating a Deployment and a Service in Kubernetes. The Deployment ensures Kibana is running and manages replicas, while the Service makes Kibana accessible.
With Kibana deployed and exposed, you can now access its interface using the IP address of any node in your cluster and the node port specified in the Service configuration (e.g., http://<node-ip>:30001).

To explore the raw logs shipped by Fluentd, you can access the Discover tab from the menu. You can use the Kibana Query Language (KQL) to search your data. However, you will first be required to specify an index pattern in order to select the data that has to be explored.

After having explored the logs, you can create dashboards to aggregate your data from various search operations. You can also import or export dashboards. Kibana dashboards are exported in the .ndjson format.

**Reminder**
Before proceeding, note that Kubernetes cluster is already up and running and that Elasticsearch and Fluentd have already been deployed within the Kubernetes cluster. These are prerequisites for deploying Kibana successfully.