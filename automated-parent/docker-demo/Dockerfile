FROM maven:3.9.1-eclipse-temurin-17 AS builder
WORKDIR /build
COPY pom.xml .
COPY docker-demo ./docker-demo
RUN cd docker-demo && mvn clean package

FROM eclipse-temurin:17-jre-alpine
WORKDIR /app
COPY --from=builder /build/docker-demo/target/docker-demo-1.0-SNAPSHOT.jar app.jar

CMD ["java", "-jar", "app.jar"]

