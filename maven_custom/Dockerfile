FROM ubuntu:18.04 AS git
RUN apt update && apt install git -y
RUN cd /tmp && git clone https://github.com/Elferey/lesson12.git

FROM maven:3.6.0-jdk-11-slim
WORKDIR /tmp
COPY --from=git  /tmp/lesson12 /tmp
RUN mvn clean && mvn install