# Use the slim (alpine) Maven image as build
FROM maven:3.5-jdk-8-alpine AS build

# Set the container application directory to /code
WORKDIR /code

# Copy pom.xml from the current folder to /code/pom.xml in the container
COPY pom.xml /code/pom.xml 
# Vérifier si cette commande est OK 

# Execute the following commands in the container :
# mvn dependency:resolve
# mvn verify
RUN dependency:resolve && mvn verify

# Copy src/main folder to /code/src/main folder in the container
COPY src/main /code/src/main

# Execute the command "mvn package" in the container
RUN mvn package
# Now change the base Docker image to openjdk 8 (you can use the jre alpine version to improve performance)
FROM openjdk:8 
# Copy from the 'build' container the produced jar : /code/target/worker-jar-with-dependencies.jar in the root path of this container : /

# Define the command to be run when launching the container
CMD ["java", "-XX:+UnlockExperimentalVMOptions", "-XX:+UseCGroupMemoryLimitForHeap", "-jar", "/worker-jar-with-dependencies.jar"]
