Deploying Kibana involves creating a Deployment and a Service in Kubernetes. The Deployment ensures Kibana is running and manages replicas, while the Service makes Kibana accessible.
With Kibana deployed and exposed, you can now access its interface using the IP address of any node in your cluster and the node port specified in the Service configuration (e.g., http://<node-ip>:30001).

To explore the raw logs shipped by Fluentd, you can access the Discover tab from the menu. You can use the Kibana Query Language (KQL) to search your data. However, you will first be required to specify an index pattern in order to select the data that has to be explored.

After having explored the logs, you can create dashboards to aggregate your data from various search operations. You can also import or export dashboards. Kibana dashboards are exported in the .ndjson format.

# Reminder
Before proceeding, note that Kubernetes cluster is already up and running and that Elasticsearch and Fluentd have already been deployed within the Kubernetes cluster. These are prerequisites for deploying Kibana successfully.