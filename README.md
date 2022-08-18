# Couchbase-Discovery

This is my sandbox to play with CouchBase

## Start

- Open this project with Gitpod: https://gitpod.io/#https://github.com/bots-garden/couchbase-discovery
- Wait a moment: the CouchBase setup is done at startup (see `.gitpod.yml`)

## Once CouchBase installed and runnning

### Create a cluster

```bash
# ------------------------------------
# Create Couchbase cluster
# ------------------------------------
couchbase-cli cluster-init -c 127.0.0.1 \
--cluster-username admin \
--cluster-password ilovepandas \
--services data,index,query \
--cluster-ramsize 4096
```

### Create a bucket

```bash
# ------------------------------------
# Create Couchbase bucket
# ------------------------------------
couchbase-cli bucket-create -c 127.0.0.1:8091 \
--username admin \
--password ilovepandas \
--bucket wasm-data \
--bucket-type couchbase \
--bucket-ramsize 1024
```

## Insert some documents

First, create a **scope**:

```bash
cbq -u admin -p ilovepandas -e "http://localhost:8091" --script='CREATE SCOPE `wasm-data`.data'
```

Then, create a **collection**:

```bash
cbq -u admin -p ilovepandas -e "http://localhost:8091" --script='CREATE COLLECTION `wasm-data`.data.docs'
```

Finally, create an index:

```bash
cbq -u admin -p ilovepandas -e "http://localhost:8091" --script='CREATE PRIMARY INDEX ON `default`:`wasm-data`.`data`.`docs`'
```

Now you can insert documents:

```bash
cbq -u admin -p ilovepandas -e "http://localhost:8091" --script='INSERT INTO `wasm-data`.data.docs (KEY, VALUE) VALUES ("key1", { "type" : "info", "name" : "John Doe" });'
cbq -u admin -p ilovepandas -e "http://localhost:8091" --script='INSERT INTO `wasm-data`.data.docs (KEY, VALUE) VALUES ("key2", { "type" : "info", "name" : "Jane Doe" });'
cbq -u admin -p ilovepandas -e "http://localhost:8091" --script='INSERT INTO `wasm-data`.data.docs (KEY, VALUE) VALUES ("key3", { "type" : "info", "name" : "Bob Morane" });'
```

cbq -u admin -p ilovepandas -e "http://localhost:8091" --script='SELECT * FROM `wasm-data`.data.docs'

