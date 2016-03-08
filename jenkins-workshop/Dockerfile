
FROM agileworks/jenkins

RUN git clone https://github.com/agileworks-tw/spring-boot-sample.git /root/workspace/spring-boot-sample
RUN cd /root/workspace/spring-boot-sample/data-rest && mvn package

ENTRYPOINT ["java", "-jar", "/opt/jenkins.war"]

CMD [""]
