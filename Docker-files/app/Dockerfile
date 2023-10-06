FROM openjdk:11 AS BUILD_IMAGE
Run apt update && apt install maven -y
RUN git clone https://github.com/nyongmac/vprofileproject.git
RUN cd vprofileproject && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="Mac"
RUN rm -rf /usr/local/tomcat/webapp/*
COPY --from=BUILD_image vprofileproject/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CM ["catalina.sh", "run"]