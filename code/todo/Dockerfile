# build stage
FROM openjdk:8-jdk-alpine3.9 as build-stage
WORKDIR /app
COPY . .
RUN ./mvnw clean package

# production stage
FROM openjdk:8-jdk-alpine3.9 as production-stage
COPY --from=build-stage app/target/todo-0.0.1-SNAPSHOT.jar app.jar
CMD java -jar app.jar
ENV SERVER_PORT 8080
EXPOSE 8080