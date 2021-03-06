
FROM ubuntu:14.04


ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update

RUN apt-get install -y wget

RUN wget --no-verbose -O /tmp/apache-maven-3.3.3.tar.gz http://archive.apache.org/dist/maven/maven-3/3.3.3/binaries/apache-maven-3.3.3-bin.tar.gz

# verify checksum
# RUN echo "87e5cc81bc4ab9b83986b3e77e6b3095 /tmp/apache-maven-3.3.3.tar.gz" | md5sum -c

# install maven
RUN tar xzf /tmp/apache-maven-3.3.3.tar.gz -C /opt/
RUN ln -s /opt/apache-maven-3.3.3 /opt/maven
RUN ln -s /opt/maven/bin/mvn /usr/local/bin
RUN rm -f /tmp/apache-maven-3.3.3.tar.gz
ENV MAVEN_HOME /opt/maven

# install git
RUN apt-get install -y git

# install nano
RUN apt-get install -y vim

# remove download archive files
RUN apt-get clean

# set shell variables for java installation
ENV java_version 1.8.0_11
ENV filename jdk-8u11-linux-x64.tar.gz
ENV downloadlink http://download.oracle.com/otn-pub/java/jdk/8u11-b12/$filename

# download java, accepting the license agreement
RUN wget --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" -O /tmp/$filename $downloadlink

RUN mkdir /opt/java-oracle && tar -zxf /tmp/$filename -C /opt/java-oracle/
ENV JAVA_HOME /opt/java-oracle/jdk$java_version
ENV PATH $JAVA_HOME/bin:$PATH

RUN update-alternatives --install /usr/bin/java java $JAVA_HOME/bin/java 20000 && update-alternatives --install /usr/bin/javac javac $JAVA_HOME/bin/javac 20000

ADD http://mirrors.jenkins-ci.org/war/1.652/jenkins.war /opt/jenkins.war
RUN chmod 644 /opt/jenkins.war
ENV JENKINS_HOME /jenkins

ENTRYPOINT ["java", "-jar", "/opt/jenkins.war"]
EXPOSE 8080

CMD [""]
