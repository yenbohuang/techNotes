# Clustering

## Key points from blogs and documents

* <http://www.hivemq.com/blog/clustering-mqtt-introduction-benefits/>
  * The single components of the MQTT broker cluster are unreliable (because everything can fail at any time, especially in cloud environments) while the whole system needs to be reliable.
  * Any TCP load balancer can be used together with HiveMQ with any load balancing algorithm.
    * Sticky sessions are not required for HiveMQ, even if persistent MQTT sessions are used.
    * MQTT clients with persistent sessions can resume their sessions at any cluster node any time, even in case of failures and network splits. 
  * Upgrading a HiveMQ cluster is as easy as it can get: Just spawn a new broker node with a new version and remove older nodes from the cluster- node by node. 
    * It's important to note that there's no need for a Blue-Green upgrade (which can be quite expensive in terms of infrastructure for huge clusters), since the clusters itself allow that different HiveMQ versions are part of the cluster while upgrading.

* <http://www.hivemq.com/clustering-hivemq-paper/>
  * Full data replication between cluster nodes is possible but is not needed.
    * Data can be distributed with configurable replica counts.
  * The HiveMQ cluster is self-healing.
    * Even if network splits occur or any kind of connectivity problem between nodes arise, the cluster as a whole is still available, as long as at least a single node is still healthy, and heals itself in error scenarios.
    * No human interaction is required in such cases.
  * HiveMQ is a MQTT Broker that is resilient against network splits and strives to be always available, even in the presence of network partitions.
    * This makes HiveMQ an eventually consistent system that strives towards consistency under normal operation and doesn't trade availability at any time.
    * An arbitrary number of broker nodes can fail or can be unavailable and the system as a whole is still online and fully functional.
  * Beside static cluster configuration it's possible to use auto-discovery mechanisms like UDP Multicast, TCP Broadcast or even more sophisticated cluster discovery mechanisms like AWS S3 discovery or Consul Discovery with off-the-shelf plugins.
  * It's easy to scale out your cluster deployments with Docker and tools like Kubernetes or Mesos (with Marathon).

## TCP/UDP multicast cluster discovery does not work in docker network

Multicast is not supported by docker for now. Refer to the following links for details:

* <https://github.com/peez80/docker-hivemq#start-on-docker-native-cluster>
* <https://github.com/docker/libnetwork/issues/552>
