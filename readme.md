# Spring Cloud Sleuth Demo

This is a demo project showing the usage of Spring Cloud Sleuth and
pushing tracing data to Zipkin.

## How to use

Run Zipkin container

```bash
docker run -d --name zipkin --restart unless-stopped -p 9411:9411 openzipkin/zipkin
```

Start two applications in different sessions:

```bash
SPRING_APPLICATION_NAME="Service A" SERVER_PORT=8081 ./mvnw spring-boot:run

SPRING_APPLICATION_NAME="Service B" SERVER_PORT=8082 ./mvnw spring-boot:run
```

Hit the endpoint to mimic tracing between services:

```bash
http :8081/api/spring-cloud-sleuth-demo/a
```

Visit the Zipkin portal to see the tracing at http://localhost:9411/zipkin/.