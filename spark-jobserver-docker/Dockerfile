FROM yanlinw/spark-jobserver:0.6.2-SNAPSHOT.mesos-0.25.0.spark-1.5.2
EXPOSE 32456-32472

# Expose driver port range (spark.driver.port + 16)

ADD ./docker.conf /app/docker.conf
# Add the docker.conf to the container
ADD ./manager_start.sh /app/manager_start.sh
# Add the docker.conf to the container
RUN chmod +x /app/manager_start.sh

ADD ./cluster-config /app/cluster-config
# Add the yarn-site.xml and hfds-site.xml to the container

ENV YARN_CONF_DIR=/app/cluster-config
# Set env variables for spark

ENV HADOOP_CONF_DIR=/app/cluster-config
# Set env variables for spark
