FROM amazoncorretto:8-alpine AS build-stage
WORKDIR /app

RUN apk update && apk add --no-cache git && \
    git clone https://github.com/spiros-k/docker-utilizing-reg.git /app && \
    adduser -D javauser && \
    apk del git && \
    chown javauser .

WORKDIR /app/spring-example-project

RUN chmod +x ./mvnw
RUN ./mvnw package -D skipTests

USER javauser

FROM openjdk:8-jdk-alpine 
WORKDIR /app/spring-example-project
COPY --from=build-stage /app/spring-example-project .

EXPOSE 8080

CMD ["sh", "-c", "java -jar ./target/docker-example-1.1.3.jar"]
