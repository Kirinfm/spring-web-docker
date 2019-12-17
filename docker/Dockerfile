# modify by https://github.com/docker-library/tomcat/blob/9ecc2f5cbaaedbe74c91cc3ecf1bab5192e741a6/8.5/jre8/Dockerfile
FROM tomcat:8.0

ENV CATALINA_HOME /usr/local/tomcat

WORKDIR $CATALINA_HOME

# start modify
RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN echo "Asia/Shanghai" > /etc/timezone

COPY webapps/*.war /usr/local/tomcat/webapps/

EXPOSE 8080
CMD ["catalina.sh", "run"]