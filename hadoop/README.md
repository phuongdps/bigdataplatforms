# Hadoop


## Installation on one node

It is necessary to configure ssh login without password for all nodes. 
```bash

$ ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa
$ cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
$ chmod 0600 ~/.ssh/authorized_keys

```

### On Mac Big Sur


Run the following command to install newest java version and hadoop on Mac OS
```bash
$ brew install hadoop
```

The command will install hadoop 3.3.0 on your Mac Big Sur and install the corresponding java - openjdk 15.0.1. After this step, you should change your JAVA_HOMEenvirnoment variable. Notably, the command /usr/libexec/java_home does not work correctly in Mac Big Sur. 

Go to your .bash_profile and put the following command to make the correct JAVA_HOME variable:
```bash
# Configuration for Hadoop
export PATH="/usr/local/opt/openjdk/bin:$PATH"
export CPPFLAGS="-I/usr/local/opt/openjdk/include"

# Add Java Home
export JAVA_HOME=/usr/local/Cellar/openjdk/15.0.1/libexec/openjdk.jdk/Contents/Home
``` 

Remember to update the information of your .bash_profile
```bash
$ source .bash_profile
```

Go to the directory "/usr/local/Cellar/hadoop/3.3.0/libexec/etc/hadoop" and modifying the required configuration files:

- hadoop-envs.sh: in this file, change the JAVA_HOME variable

```bash
export JAVA_HOME=/usr/local/Cellar/openjdk/15.0.1/libexec/openjdk.jdk/Contents/Home
```

- core-site.xml: in this file, put the following configuration
```bash

<!-- Put site-specific property overrides in this file. -->
<configuration>
    <property>
        <name>fs.defaultFS</name>
        <value>hdfs://localhost:9000</value>
    </property>
</configuration>

```

- hdfs-site.xml: in this file, put the following configuration
```bash

<!-- Put site-specific property overrides in this file. -->

<configuration>
    <property>
        <name>dfs.replication</name>
        <value>1</value>
    </property>
</configuration>
```

- mapred-site.xml: do later



At this time, you can start hadoop services and use them.
```bash
# format file system
$ cd /usr/local/opt/hadoop
$ hdfs namenode -format

# Go to the corresponding directory
$ cd /usr/local/opt/hadoop/sbin

# start all services
$ ./start-all.sh

# Run JPS to check the services
$ jps

# to stop all services
$ ./stop-all.sh

```


## Installation on a cluster
