# build freerouting jar
FROM openjdk:18-slim AS builder
RUN apt-get update && apt-get -y install wget bzip2 make
# RUN wget http://repo.hu/projects/freerouting_cli/releases/freerouting_cli-1.tar.bz2
# RUN tar xjf freerouting_cli-1.tar.bz2
# WORKDIR freerouting_cli-1
# RUN make
RUN wget http://repo.hu/projects/freerouting_cli/releases-jar/freerouting_cli-1.tar.gz
RUN tar -xzf freerouting_cli-1.tar.gz

# build native image
FROM ghcr.io/graalvm/graalvm-ce:latest@sha256:5a200da297ce846b718c56619aeaf1204686587c4bc9979d37b2c4ffd10e0806  as build-native
RUN gu install native-image

# https://www.graalvm.org/reference-manual/native-image/StaticImages/
RUN mkdir musl
RUN curl https://more.musl.cc/10.2.1/x86_64-linux-musl/x86_64-linux-musl-native.tgz --output musl.tgz
RUN tar -xzf musl.tgz -C musl --strip-components 1
RUN mkdir zlib
RUN curl https://zlib.net/zlib-1.2.12.tar.gz --output zlib.tar.gz
RUN tar -xzf zlib.tar.gz -C zlib --strip-components 1

ENV CC=/musl/bin/gcc
ENV PATH="/musl/bin:${PATH}"

WORKDIR zlib
RUN ./configure --prefix=../musl --static
RUN make
RUN make install
WORKDIR /

COPY --from=builder /freerouting_cli/lib/freerouting_cli.jar /app/freerouting_cli.jar
RUN cd /app; native-image --no-fallback --static --libc=musl -jar freerouting_cli.jar

# freerouting image
FROM alpine:3.15.4@sha256:4edbd2beb5f78b1014028f4fbb99f3237d9561100b6881aabbf5acce2c4f9454
COPY --from=build-native /app/freerouting_cli /bin/freerouting_cli
