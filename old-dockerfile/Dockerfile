FROM amazoncorretto:8
WORKDIR /app

RUN yum update -y && yum install -y git && yum install -y maven 
RUN git clone https://github.com/spiros-k/docker-utilizing-reg.git /app

WORKDIR /app/spring-example-project

RUN chmod +x ./mvnw
RUN ./mvnw package -DskipTests

EXPOSE 8080
CMD ["sh", "-c", "java -jar ./target/docker-example-1.1.3.jar"]
