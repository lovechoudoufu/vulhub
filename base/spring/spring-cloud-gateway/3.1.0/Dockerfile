FROM maven:3-jdk-8 AS builder

COPY ./ /usr/src

RUN cd /usr/src; \
    mvn -U clean package -Dmaven.test.skip=true -Dmaven.artifact.threads=10

FROM openjdk:8-jre

LABEL maintainer="phithon <root@leavesongs.com>"

COPY --from=builder /usr/src/target/spring-cloud-gateway-0.0.1-SNAPSHOT.jar /spring-cloud-gateway-0.0.1-SNAPSHOT.jar

CMD ["java", "-Djava.security.egd=file:/dev/./urandom", "-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005", "-jar", "/spring-cloud-gateway-0.0.1-SNAPSHOT.jar"]
