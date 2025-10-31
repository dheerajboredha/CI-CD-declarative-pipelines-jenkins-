FROM maven:3.9.11-eclipse-temurin-17-alpine AS maven_build
RUN apk add git
RUN git clone https://github.com/dheerajboredha/spring-petclinic.git && \
    cd spring-petclinic && \
    mvn package

FROM openjdk:25-ea-17-jdk-slim AS java_run
LABEL project="my_sample_app"
RUN useradd -m -d /usr/share/app -s /bin/bash dheeraj
USER dheeraj
WORKDIR /usr/share/app
COPY --from=maven_build /spring-petclinic/target/*.jar app.jar
EXPOSE 8080/tcp
CMD ["java","-jar","app.jar"]
