FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone --branch docker https://github.com/cetyl/Vprofile-Project.git
RUN cd vprofile-project && mvn install 



FROM tomcat:8-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="Rohan"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war


EXPOSE 8080
CMD ["catalina.sh","run"]