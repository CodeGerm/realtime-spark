FROM sequenceiq/hadoop-docker
MAINTAINER yanlinw
ADD spark-assembly-1.5.2-hadoop2.6.0.jar /spark-assembly-1.5.2-hadoop2.6.0.jar
ADD yarn-site.xml /usr/local/hadoop/etc/hadoop/yarn-site.xml
RUN service sshd start && $HADOOP_PREFIX/etc/hadoop/hadoop-env.sh && $HADOOP_PREFIX/sbin/start-dfs.sh && sleep 90 && $HADOOP_PREFIX/bin/hdfs dfs -mkdir -p /spark_jars
RUN service sshd start && $HADOOP_PREFIX/etc/hadoop/hadoop-env.sh && $HADOOP_PREFIX/sbin/start-dfs.sh && sleep 90 && $HADOOP_PREFIX/bin/hdfs dfs -put /spark-assembly-1.5.2-hadoop2.6.0.jar  /spark_jars/spark-assembly-1.5.2-hadoop2.6.0.jar
