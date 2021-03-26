FROM maven:3.5-jdk-8-alpine AS builder

WORKDIR /builder

COPY pom.xml .

RUN mvn dependency:resolve

COPY src ./src

RUN mvn package

FROM openjdk:8-jre-alpine

WORKDIR /jar

COPY --from=builder /builder .

CMD ["java", "-jar", "target/worker-jar-with-dependencies.jar"]