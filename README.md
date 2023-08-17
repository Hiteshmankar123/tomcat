# tomcat
FROM centos
RUN cd /etc/yum.repos.d/
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
RUN yum -y install java
RUN mkdir /opt/tomcat
WORKDIR /opt/tomcat
ADD   https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.92/bin/apache-tomcat-8.5.92.tar.gz .
RUN tar xvzf apache-tomcat-8.5.92.tar.gz
RUN mv apache-tomcat-8.5.92/* /opt/tomcat
EXPOSE 8080
CMD ["/opt/maven/bin/catalina.sh","run"]
