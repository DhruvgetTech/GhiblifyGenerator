# Use an official Maven image to build the app
FROM maven:3.9.6-eclipse-temurin-21 AS build

# Set the working directory in the container
WORKDIR /app

# Copy the project files
COPY . .

# Build the application
RUN mvn clean package -DskipTests

# Use a lightweight JDK image to run the app
FROM eclipse-temurin:21-jdk

# Set the working directory in the new image
WORKDIR /app

# Copy the jar file from the build stage
COPY --from=build /app/target/*.jar app.jar

# Expose port 8080
EXPOSE 8080

# Run the Spring Boot app
ENTRYPOINT ["java", "-jar", "app.jar"]

