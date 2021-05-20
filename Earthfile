
FROM alpine:3.13

source:
    WORKDIR /source
    COPY --dir * ./
    SAVE ARTIFACT /source/*

requirements:
    WORKDIR /reqs
    COPY ./.requirements /reqs/
    SAVE ARTIFACT /reqs/.requirements

sha:
    WORKDIR /sha
    ARG EARTHLY_GIT_HASH
    RUN echo "$EARTHLY_GIT_HASH" >./sha
    SAVE ARTIFACT ./sha

version:
    WORKDIR /version
    COPY ./kong-*.rockspec /version/
    RUN echo ./kong-*.rockspec | sed 's,.*/,,' | cut -d- -f2 > ./version
    SAVE ARTIFACT ./version
