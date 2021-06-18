# Hadoop Installation in Google Cloud / Ubuntu Desktop / WSL

1.	Virtual Machine -> Ubuntu 20.04 (Allow HTTP and HTTPS Traffic) (Only for GCP)
2.	wget https://downloads.apache.org/hadoop/common/hadoop-3.2.2/hadoop-3.2.2.tar.gz
3.	tar –xvf hadoop-3.2.2.tar.gz
4.	sudo apt-get update (Update the package list)
5.	sudo apt install openjdk-8-jdk (Apache Hadoop from 3.0.x to 3.2.x now supports only Java 8)
6.	sudo update-alternatives --config java (To get Path of Java)
/usr/lib/jvm/java-8-openjdk-amd64  (Only HOME Folder)
7.	Edit  hadoop/etc/hadoop/hadoop-env.sh  (Note Spaces after = )
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export HADOOP_HOME=/home/sdmphdcusat/hadoop
8.	Pseudo-Distributed Operation: Hadoop can also be run on a single-node in a pseudo-distributed mode where each Hadoop daemon runs in a separate Java process.
9.	Configurations:  etc/hadoop/core-site.xml, etc/hadoop/hdfs-site.xml
10.	ssh localhost
11.	ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
chmod 0600 ~/.ssh/authorized_keys
12.	Try ssh localhost
13.	bin/hdfs namenode –format (Name Node Format)
14.	sbin/start-dfs.sh  (rm -rf /tmp/hadoop-sdmphdcusat) If data node is not starting
15.	Visit Name Node: http://localhost:9870/
16.	bin/hdfs dfs -mkdir /input
17.	bin/hdfs dfs -put test.dat /input
18.	bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-3.2.2.jar wordcount /input /output
19.	bin/hdfs dfs -ls /
20.	bin/hdfs dfs -get /output3 output4
