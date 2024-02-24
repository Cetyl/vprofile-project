FROM openjdk:11 AS BUILD_IMAGE
 
 
# Installing Services
RUN apt update && apt install maven -y
# Cloning The Repo
RUN git clone "https://github.com/cetyl/Vprofile-Project.git"
# Building The Artifact
WORKDIR /Vprofile-Project
RUN git checkout containers && mvn install
 
FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE Vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]