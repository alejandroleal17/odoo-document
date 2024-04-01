# ScyllaDB

ScyllaDB is an open-source, highly performant, distributed NoSQL database. It's designed to handle large amounts of data with low latency and is compatible with Apache Cassandra, making it a popular choice for real-time big data applications.

ScyllaDB is integrated into our Navigator Platform, running in GKE and managed through ArgoCD. It's not exposed to the internet for security reasons. To interact with ScyllaDB, we need to be within the GKE cluster, typically using a test pod.

## Steps to test the connection from any namespace:


1. First, make sure you are testing using a pod inside the kubernetes cluster
2. Install the correct driver (In this example we will use python)
See [here](https://python-driver.docs.scylladb.com/stable/installation.html)
3. Set up a test script to verify the connection 
See [here](https://python-driver.docs.scylladb.com/stable/getting-started.html)
4. Use the scylladb service URL for the cluster connection

    - URL: `scylladb-client.scylla.svc.cluster.local`

5. Full script to verify the connection:

    ```python
    from cassandra.cluster import Cluster

    print("starting")
    cluster = Cluster(['scylladb-client.scylla.svc.cluster.local'])

    print("connecting")
    session = cluster.connect()
    print("connected")
    ```

6. Run this script inside the pod and the connection should be ready to use scylladb using the cassandra driver!