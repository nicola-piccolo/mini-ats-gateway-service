FROM openjdk:12-jdk-alpine

RUN addgroup -S gateway-service && adduser -S gateway-service -G gateway-service

ENV HOME_DIRECTORY="/home/gateway-service"
ENV LOGS_DIRECTORY="$HOME_DIRECTORY/logs"

USER gateway-service:gateway-service

RUN mkdir $LOGS_DIRECTORY

ARG DEPENDENCY=target/dependency

COPY ${DEPENDENCY}/BOOT-INF/lib /app/lib
COPY ${DEPENDENCY}/META-INF /app/META-INF
COPY ${DEPENDENCY}/BOOT-INF/classes /app

ENTRYPOINT ["java","-cp","app:app/lib/*","org.miniats.gatewayservice.GatewayServiceApplication"]