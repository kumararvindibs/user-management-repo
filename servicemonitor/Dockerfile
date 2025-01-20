# Use an official Maven image to build the project
FROM maven:3.8.7-openjdk-18 AS build

# Set the working directory in the container
WORKDIR /app

# Copy the pom.xml file and download the dependencies
COPY . .
RUN mvn clean install


# Use an official OpenJDK runtime as a parent image
FROM openjdk:18-jdk-slim

# Set the working directory in the container
WORKDIR /app

# Copy the built jar file from the build stage
COPY --from=build /app/target/servicemonitor-0.0.1-SNAPSHOT.jar /app/servicemonitor.jar

# Expose port 8080 for the application
EXPOSE 8989

# Run the application when the container launches
CMD ["java", "-jar", "servicemonitor.jar"]