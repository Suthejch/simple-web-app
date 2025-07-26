# Build stage - where we compile our application
FROM maven:3.8.3-openjdk-11 AS build
COPY . .
RUN mvn clean package

# Run stage - where we create the final lightweight image
FROM openjdk:11-jre-slim
COPY --from=build /target/simple-web-app-0.0.1-SNAPSHOT.jar /app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app.jar"]