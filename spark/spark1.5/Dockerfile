FROM jhu/java:jdk8

ENV SPARK_Version 1.5.2
ENV Hadoop_Version 2.4
ENV SPARK_PACKAGE ${SPARK_Version}-bin-hadoop${Hadoop_Version}
ENV SPARK_HOME /opt/spark-"${SPARK_PACKAGE}"

# Update the base ubuntu image with dependencies needed for Spark
# Get spark and put into /opt/spark-"${SPARK_VERSION}"-bin-hadoop"${Hadoop_Version}"
# RUN curl --silent --retry 3 --location http://apache.fayea.com/spark/spark-"${SPARK_Version}"/spark-"${SPARK_PACKAGE}".tgz \
RUN yum install -y python && \
    curl --silent --retry 3 --location "http://www.apache.org/dyn/closer.lua?filename=spark/spark-${SPARK_Version}/spark-${SPARK_PACKAGE}.tgz&action=download"  \
    | tar -xzC /opt && rm -fr ${SPARK_HOME}/lib/spark-examples*.jar ${SPARK_HOME}/examples && \
    yum clean all

