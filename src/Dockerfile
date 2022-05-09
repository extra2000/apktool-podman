FROM docker.io/openjdk:8-jdk-bullseye

COPY ./apktool /opt/apktool
WORKDIR /opt/apktool

RUN ./gradlew build shadowJar
