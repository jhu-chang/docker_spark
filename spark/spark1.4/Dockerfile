# This is an example Dockerfile for creating a Spark image which can be
# references by the Spark property 'spark.mesos.executor.docker.image'
#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

FROM jhu/java:jdk8

ENV SPARK_Version 1.4.1
ENV Scala_Bin_Version 2.10
ENV Hadoop_Version 2.4
ENV SPARK_PACKAGE ${SPARK_Version}-bin-hadoop${Hadoop_Version}

# Update the base ubuntu image with dependencies needed for Spark
# Get spark and put into /opt/spark-"${SPARK_VERSION}"-bin-hadoop"${Hadoop_Version}"
# RUN curl --silent --retry 3 --location http://www.apache.org/dyn/closer.lua/spark/spark-"${SPARK_Version}"/spark-"${SPARK_PACKAGE}".tgz \
RUN  yum install -y python && \
     curl --silent --retry 3 --location http://apache.fayea.com/spark/spark-"${SPARK_Version}"/spark-"${SPARK_PACKAGE}".tgz \
     | tar -xzC /opt
ENV SPARK_HOME /opt/spark-"${SPARK_PACKAGE}"

