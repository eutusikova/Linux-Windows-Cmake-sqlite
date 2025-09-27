FROM alpine:3.16

RUN apk update && apk add --no-cache build-base unzip
WORKDIR /build
COPY sqlite-amalgamation-3260000.zip .
RUN unzip sqlite-amalgamation-3260000.zip
WORKDIR /build/sqlite-amalgamation-3260000
RUN gcc -shared -fPIC -o sqlite3.so sqlite3.c
RUN cp sqlite3.so /build/sqlite3.so
WORKDIR /build
