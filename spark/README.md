# Spark Standalone Cluster
In this tutorial, we will setup a Spark Cluster with a master node (node1) and 2 slave nodes (node2 and node3).

## Installation
* Launch 3 machines on the Openstack CSC Cloud: node1, node2 and node3 (ubuntu 20.04). Configuring nodename, IP addresses and /etc/hosts. Then configure ssh without password for all machines.

* Install the python3, pip3 on each machine and create a virtual python environment.  
```bash
$ mkdir environments
$ cd environments
$ python3 -m venv myenv
$ source myenv/bin/activate

```

In order to have this virtual environment available for running spark. It is recommended that you activate it every time login to the machines. Add the following lines into your .bashrc file in each machine.
```bash


```


* Install spark
```bash


```

### Master node


### Slave node



## Example Programs
