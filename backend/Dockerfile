# Stage 1: Build Spring Boot application
FROM eclipse-temurin:21-jdk AS build

# Set working directory
WORKDIR /app

# Copy backend project
COPY . .

# Make Maven wrapper executable
RUN chmod +x mvnw

# Build Spring Boot application
RUN ./mvnw clean package -DskipTests


# Stage 2: Run Spring Boot application
FROM eclipse-temurin:21-jre

# Set working directory
WORKDIR /app

# Copy generated JAR from build stage
COPY --from=build /app/target/*.jar app.jar

# Spring Boot default port
EXPOSE 8080

# Start application
ENTRYPOINT ["java", "-jar", "app.jar"]