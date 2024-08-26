The EFK stack combines Elasticsearch, Fluentd, and Kibana to aggregate, store, and visualize logs from multiple sources within a Kubernetes environment.

Components of the EFK Stack
- Elasticsearch 🔎: A distributed, RESTful search and analytics engine capable of addressing a growing number of use cases.

- Fluentd 🚿: An open-source data collector for unified logging, which allows you to unify data collection and consumption for better use and understanding of data.

- Kibana 📊: A visualization layer that works on top of Elasticsearch, providing a user-friendly interface to visualize data.


Deploying the EFK stack on Kubernetes involves setting up each component to work together seamlessly. There are multiple ways of deploying the stack like manual deployment, helm charts, operators and pre-built cloud marketplace solutions. In this course, we will follow the manual deployment approach using individual manifest files.

# step 1 : Deploy Elasticsearch 

Elasticsearch - the backend of the EFK stack - is basically a Document-based NoSQL database that runs on port 9200 by default.
Elasticsearch doesn't just store data but also ensures data durability and failure recovery by utilizing replication. To ensure quick availability of data, it utilizes sharding in addition to replication.
In an elasticsearch cluster, its the master node that coordinates actions and manages changes.

# setp 2 : Deploy Fluentd

Fluentd - the log shipper - utilizes a variety of plugins for filtering and transforming log data. These plugins are defined in the fluentd configuration file, which uses the .conf extension.
Fluentd uses memory buffering mechanism to ensure reliable log delivery to Elasticsearch.

# step 3 : Deploy Kibana

Kibana - the visualization wizard - provides extensive data presentation capabilities through graphs and charts and runs on port 5601 by default.