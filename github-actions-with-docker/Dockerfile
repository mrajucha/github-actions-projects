# Use the adoptopenjdk/openjdk11:alpine-jre as the base image
FROM adoptopenjdk/openjdk11:alpine-jre

# Set the working directory inside the container
WORKDIR /app

# Copy your Java application JAR file into the container
COPY target/Java-demo-app.jar /app/Java-demo-app.jar

# Define the command to run your Java application
CMD ["java", "-jar", "Java-demo-app.jar"]


# Expose port to check
EXPOSE 8088