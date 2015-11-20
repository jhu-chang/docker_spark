FROM jhu/java:jdk8

ENV SPARK_Version 1.5.2
ENV Scala_Bin_Version 2.10
ENV Hadoop_Version 2.4

# Update the base ubuntu image with dependencies needed for Spark
RUN  yum install -y python libnss3 

# Get spark and put into /opt/spark-"${SPARK_VERSION}"-bin-hadoop"${Hadoop_Version}"
RUN curl http://www.apache.org/dyn/closer.lua/spark/spark-"${SPARK_VERSION}"/spark-"${SPARK_VERSION}"-bin-hadoop"${Hadoop_Version}".tgz \
    | tar -xzC /opt
ENV SPARK_HOME /opt/spark-"${SPARK_VERSION}"-bin-hadoop"${Hadoop_Version}"

