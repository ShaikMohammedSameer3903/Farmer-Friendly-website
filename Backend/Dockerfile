# FROM maven:3.8.5-openjdk-17 AS build
# COPY . .
# RUN mvn clean package -DskipTests
# FROM openjdk:17.0.1-jdk-slim
# COPY --from=build target/Backend-0.0.1-SNAPSHOT.jar /app.jar
# EXPOSE 8080
# ENTRYPOINT ["java", "-jar", "/app.jar"]
# Stage 1: Build the JAR file
FROM maven:3.8.4-openjdk-17 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Stage 2: Run the JAR file
FROM openjdk:17.0.1-jdk-slim
COPY --from=build /app/target/Backend-0.0.1-SNAPSHOT.jar /app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app.jar"]
