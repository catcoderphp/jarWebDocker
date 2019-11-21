# JAR WEB DOCKER

# Generating a Dockerfile

```dockerfile
FROM openjdk:8-jdk-alpine
VOLUME /tmp
ARG JAR_FILE
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```
The ```JAR_FILE``` could be passed in as part of the docker command (it will be different for Maven and Gradle). E.g. for Maven:
```bash
$ docker build --build-arg JAR_FILE=target/*.jar -t application/app_name .
```
and for Gradle:
```bash
$ docker build --build-arg JAR_FILE=build/libs/*.jar -t application/app_name .
```
Then we can simply build an image with:
```bash
$ docker build -t application/app_name .
````
