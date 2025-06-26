# Use Eclipse Temurin (Java 21) base image
FROM eclipse-temurin:21-jdk

# Set working directory
WORKDIR /app

# Copy your application JAR into the image
COPY target/search-service-1.0-SNAPSHOT.jar /app/search-service-1.0-SNAPSHOT.jar

# Expose a port (optional, change as needed)
EXPOSE 7070

# Default command to run your JAR
ENTRYPOINT ["java", "-jar", "/app/search-service-1.0-SNAPSHOT.jar"]