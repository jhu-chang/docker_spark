FROM centos:centos6.7
#FROM daocloud.io/centos:6.7
MAINTAINER Jie Hu <gt.hu.chang@gmail.com >

ENV VERSION 8
ENV UPDATE 60
ENV BUILD 27

ENV JAVA_HOME /usr/lib/jre/java-${VERSION}-oracle
COPY GeoTrust_Global_CA.pem /tmp/
RUN yum install -y ca-certificates curl tar && \
	curl --silent --location --retry 3 --cacert /tmp/GeoTrust_Global_CA.pem \
	--header "Cookie: oraclelicense=accept-securebackup-cookie;" \
    http://download.oracle.com/otn-pub/java/jdk/"${VERSION}"u"${UPDATE}"-b"${BUILD}"/jre-"${VERSION}"u"${UPDATE}"-linux-x64.tar.gz \
	| tar xz -C /tmp && \
	mkdir -p /usr/lib/jre && mv /tmp/jre1.${VERSION}.0_${UPDATE} "${JAVA_HOME}" && \
	yum clean all && \
	rm -rf /tmp/* /var/tmp/*


RUN update-alternatives --install "/usr/bin/java" "java" "${JAVA_HOME}/bin/java" 1 && \
	update-alternatives --install "/usr/bin/javaws" "javaws" "${JAVA_HOME}/bin/javaws" 1 && \
	update-alternatives --set java "${JAVA_HOME}/bin/java" && \
	update-alternatives --set javaws "${JAVA_HOME}/bin/javaws"
