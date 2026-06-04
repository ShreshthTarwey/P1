FROM maven:3.9.1-eclipse-temurin-17 AS builder
WORKDIR /build
COPY pom.xml .
COPY src ./src
COPY mvnw .
COPY .mvn ./.mvn
RUN chmod +x mvnw
RUN ./mvnw clean package

FROM eclipse-temurin:17-jre-alpine
WORKDIR /app
COPY --from=builder /build/target/docker-demo-1.0-SNAPSHOT.jar app.jar

CMD ["java", "-jar", "app.jar"]
