# Use the official Maven image as the build stage
FROM maven:3.9.12-eclipse-temurin-25 AS build

WORKDIR /app

COPY pom.xml .
COPY src ./src

RUN mvn clean package -DskipTests

# Use a smaller base image for the runtime stage
FROM eclipse-temurin:25-jre-alpine

WORKDIR /app

# Copy the built JAR file from the build stage
COPY --from=build /app/target/*.jar ./app.jar

# ENTRYPOINT er ændret fra "-jar app.jar" til "-cp app.jar Main"
ENTRYPOINT ["java", "-cp", "app.jar", "Main"]
