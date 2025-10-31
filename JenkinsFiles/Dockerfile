FROM maven:3.9.11-ibm-semeru-17-noble AS build
RUN git clone https://github.com/dheerajboredha/spring-petclinic.git && \
    cd spring-petclinic &&  ./mvnw package
FROM openjdk:26-trixie AS runtime
RUN adduser -m -d /usr/share/demo -s /bin/bash testuser
USER testuser
WORKDIR /usr/share/demo
copy --from=build /spring-petclinic/target/spring-petclinic.jar  kishore .jar
EXPOSE 8080/tcp
CMD ["java","-jar","kishore.jar"]