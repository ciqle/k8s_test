# First stage: Build stage
# Using full OpenJDK 11 image as the build environment
FROM openjdk:11 AS buildstage
# Copy application source code into the image
COPY . /app
# Set the working directory
WORKDIR /app
# Compile the Java source code
RUN javac Hello.java

# Second stage: Runtime stage
# Using a smaller JRE-only image to reduce final size
FROM openjdk:11-jre-slim
# Copy only the compiled class file from the build stage
COPY --from=buildstage /app/Hello.class /app/
# Set the working directory
WORKDIR /app

# Define the command to run when the container starts
# Docker will run this as /bin/sh -c "java Hello"
# which means sh will be the process with PID 1
# SIGTERM will be sent to sh, not java
# This is not ideal for signal handling

# CMD java Hello

CMD ["java", "Hello"]
# This is the preferred way to run Java applications in Docker
# because it avoids the shell and directly runs the Java process.
# This is important for signal handling and process management.