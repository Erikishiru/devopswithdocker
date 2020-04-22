FROM openjdk:8

WORKDIR /spring-example-project
COPY . .
RUN ./mvnw package

ENTRYPOINT java -jar ./target/docker-example-1.1.3.jar