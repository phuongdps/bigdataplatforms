# Spark Standalone Cluster
In this tutorial, we will setup a Spark Cluster with a master node (node1) and 2 slave nodes (node2 and node3).

## Installation
* Launch 3 machines on the Openstack CSC Cloud: node1, node2 and node3 (ubuntu 20.04). Configuring nodename, IP addresses and /etc/hosts. Then configure ssh without password for all machines.

* Install the python3, pip3 on each machine and create a virtual python environment.  
```bash
# python3 is installed by default in ubuntu 20.04
$ sudo apt update
$ sudo apt -y upgrade
$ sudo apt install -y python3-pip
$ sudo apt install -y build-essential libssl-dev libffi-dev python3-dev
$ sudo apt install -y python3-venv

# Create a separate "environments"" folder
$ mkdir environments
$ cd environments
$ python3 -m venv myenv
$ source myenv/bin/activate

# Install java and scala
$ sudo apt install default-jdk
$ sudo apt-get install -y software-properties-common
$ sudo apt-get install scala

```

In order to have this virtual environment available for running spark. It is recommended that you activate it every time login to the machines. Add the following line into your .bashrc file in each machine.
```bash
source ~/environments/myenv/bin/activate
```


* Install spark

Firstly, download the newest version of spark at the website[http://spark.apache.org/downloads.html]. For example, spark-3.0.1 such as follows
```bash
# Install spark
$ cd environments
$ wget https://mirror-2.hosthink.net/apache/spark/spark-3.0.1/spark-3.0.1-bin-hadoop2.7.tgz
$ tar zxf spark-3.0.1-bin-hadoop2.7.tgz
$ mv spark-3.0.1-bin-hadoop2.7 spark

# Configure spark conf for each node both master and slave are the same
$ cd spark/conf
$ cp spark-env.sh.template spark-env.sh

```

Secondly, assign the SPARK_MASTER_HOST variable in the spark-env.sh file with the master IP address in each machine or node.
```bash

SPARK_MASTER_HOST=192.168.1.15

```

Finally, the cluster is ready for launching spark. Just execute the corresponding shell script on the nodes.

### Master node
Start the master shell script
```bash
# start the master
$ spark/sbin/start-master.sh

# stop the master
$ spark/sbin/stop-master.sh
```

### Slave node
Start the slave shell script
```bash
# start this node as a slave
$ spark/sbin/start-slave.sh

# stop this node
$ spark/sbin/stop-slave.sh
```

At this stage, everything is done and your spark cluster is ready to run the programs.

## Example Programs
In the examples folder of the spark directory, there are lots of example programs. For example, to run the pi.py program on our spark cluster, you just run the following command:

```bash

$ bin/spark-submit --master spark://192.168.1.15:7077 examples/src/main/python/pi.py 1000

```

For checking the status of your spark cluster, go to the URL[http://public_IP_of_Master_Node:8080].
