FROM golang:1.23.3

RUN groupadd --gid 1000 dev && \
    useradd --uid 1000 --gid dev --shell /bin/bash --create-home dev

RUN set -eux; \
    apt-get update; \
    apt-get install -y --no-install-recommends \
        vim \
        bash-completion \
        protobuf-compiler; \
    rm -rf /var/lib/apt/lists/*

USER dev

RUN set -eux; \
    go install google.golang.org/protobuf/cmd/protoc-gen-go@latest; \
    go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest

ENV PATH=$PATH:$GOPATH/bin
