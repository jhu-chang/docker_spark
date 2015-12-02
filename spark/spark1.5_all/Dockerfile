FROM centos:centos6.7
#FROM daocloud.io/centos:6.7
MAINTAINER Jie Hu <gt.hu.chang@gmail.com >

ENV VERSION 8
ENV UPDATE 60
ENV BUILD 27
ENV SPARK_Version 1.5.2
ENV Hadoop_Version 2.4
ENV SPARK_PACKAGE ${SPARK_Version}-bin-hadoop${Hadoop_Version}
ENV SPARK_HOME /opt/spark-"${SPARK_PACKAGE}"

ENV JAVA_HOME /usr/lib/jdk/java-${VERSION}-oracle

COPY GeoTrust_Global_CA.pem /tmp/
# yum update -y &&
RUN  yum install -y ca-certificates curl tar python && \
	curl --silent --location --retry 3 --cacert /tmp/GeoTrust_Global_CA.pem \
	--header "Cookie: oraclelicense=accept-securebackup-cookie;" \
	http://download.oracle.com/otn-pub/java/jdk/"${VERSION}"u"${UPDATE}"-b"${BUILD}"/jdk-"${VERSION}"u"${UPDATE}"-linux-x64.tar.gz \
	| tar xz -C /tmp && \
	mkdir -p /usr/lib/jdk && mv /tmp/jdk1.${VERSION}.0_${UPDATE} "${JAVA_HOME}" && \
	yum clean all && \
	rm -rf /tmp/* /var/tmp/* && \
    update-alternatives --install "/usr/bin/java" "java" "${JAVA_HOME}/bin/java" 1 && \
	update-alternatives --install "/usr/bin/javaws" "javaws" "${JAVA_HOME}/bin/javaws" 1 && \
	update-alternatives --install "/usr/bin/javac" "javac" "${JAVA_HOME}/bin/javac" 1 && \
	update-alternatives --set java "${JAVA_HOME}/bin/java" && \
	update-alternatives --set javaws "${JAVA_HOME}/bin/javaws" && \
	update-alternatives --set javac "${JAVA_HOME}/bin/javac" && \
    curl --silent --retry 3 --location "http://www.apache.org/dyn/closer.lua?filename=spark/spark-${SPARK_Version}/spark-${SPARK_PACKAGE}.tgz&action=download" \
    | tar -xzC /opt && rm -fr ${SPARK_HOME}/lib/spark-examples*.jar ${SPARK_HOME}/examples

