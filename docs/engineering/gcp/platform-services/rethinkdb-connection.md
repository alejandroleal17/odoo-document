# RethinkDB

RethinkDB is the open-source, scalable database that makes building realtime apps dramatically easier.

We have RethinkDB integrated into the Navigator Platform, which is running in GKE and managed through ArgoCD. As of today, it is not exposed to the internet (and it most likely never will be), so in order to connect to it, we must be within the GKE cluster (e.g., using a test pod).

## Steps to test the connection from any namespace:


1. Ensure that you are conducting the test using a pod inside the Kubernetes cluster.
2. Install the correct driver (for this example, we will use Python). For instructions, see [here](https://rethinkdb.com/docs/install-drivers/python/).
3. Set up a test script to verify the connection. Instructions can be found [here](https://rethinkdb.com/docs/install-drivers/python/) in the Usage section.
4. Use the rethinkdb service URL for the cluster connection and the default password

    - URL: `rethinkdb-rethinkdb-cluster.rethinkdb.svc.cluster.local`
    - Password: `rethinkdb`

5. Full script to verify the connection:

    ```python
    from rethinkdb import r

    r.connect('rethinkdb-rethinkdb-cluster.rethinkdb.svc.cluster.local', password="rethinkdb").repl()
    r.db('test').table_create('tv_shows').run()
    r.table('tv_shows').insert({ 'name': 'Star Trek TNG' }).run()
    ```

6. Run this script inside the pod and the connection should be ready to use the rethinkdb driver
