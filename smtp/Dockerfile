FROM alpine:3.6

RUN apk add --no-cache ca-certificates openssl \
    ruby ruby-bigdecimal ruby-json sqlite-libs libstdc++

RUN apk add --no-cache --virtual .build-deps \
        ruby-dev make g++ sqlite-dev \
        && gem install mailcatcher --no-ri --no-rdoc \
        && apk del .build-deps \
        && rm -rf /var/cache/apk/*

# smtp port & web port
EXPOSE 1025 1080

ENTRYPOINT ["mailcatcher"]
CMD ["--foreground", "--ip=0.0.0.0"]
