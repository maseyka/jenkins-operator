FROM alpine:3.8

ENV OPERATOR=/usr/local/bin/jenkins-operator \
    USER_UID=1001 \
    USER_NAME=jenkins-operator \
    HOME=/home/jenkins-operator

RUN apk add --no-cache ca-certificates openssh-client

# install operator binary
COPY jenkins-operator ${OPERATOR}

COPY bin /usr/local/bin
COPY configs /usr/local/configs

RUN chmod u+x /usr/local/bin/user_setup && \
    chmod ugo+x /usr/local/bin/entrypoint && \
    /usr/local/bin/user_setup

ENTRYPOINT ["/usr/local/bin/entrypoint"]

USER ${USER_UID}
