# Docker - Data Science Using Spark and MLFlow Tracking

Jupyter with Spark Magics accessing Spark Standalone Cluster using Apache Livy. Metastore Data will be shared by Spark and Hive using a MYSQL database backend store. MLFLow Tracking server is also available and uses a local sqlite db backend within its container. Polynote is also available.

Merging Sparkmagic with Spark Hive Metastore docker projects.
This repo is combines several reference repos
* forked from https://github.com/amesar/docker-spark-hive-metastore
* polynote from https://github.com/xtreamsrl/polynote-docker 
* mlflow from https://github.com/crmne/mlflow-tracking 
* Jupyter with Spark Magics from https://github.com/jupyter-incubator/sparkmagic

### Overview

**Files**
  * [docker-compose.yml](docker-compose.yml) - Docker compose file
  * Dockerfile.* - per different container
  * [conf/hive/hive-site.xml](conf/hive-site.xml) - Shared between Spark and Hive. Lives in /opt/spark/conf and /opt/hive/conf.

**Persisting Data**

In order to save data between container runs, we use Docker's volume feature to persist data to the host disk in the directory 'container_data'.
 * container_data/mysql - MySQL data from /var/lib/mysql
 * container_data/spark/warehouse - /shared_data/hive/warehouse - hive.metastore.warehouse.dir
 * container_data/hive/warehouse - /shared_data/hive/warehouse - hive.metastore.warehouse.dir

### Build the containers
```
docker-compose -f docker-compose.yml build
```

### Launch the containers

```
docker-compose -f docker-compose.yml up -d
```
