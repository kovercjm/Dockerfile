# -------------------------------------------------
# Base image for Golang development environment
#
# Author: Kover CHENG (jueming.cheng@gmail.com)
# Updated: 30 Aug 2023
# -------------------------------------------------

ARG GOLANG_VERSION=latest
FROM golang:${GOLANG_VERSION}

RUN DEBIAN_FRONTEND="noninteractive" \
    apt update && \
    apt install --no-install-recommends -y \
      ca-certificates \
      git \
      make && \
    rm -rf /var/lib/apt/lists/*

RUN go env -w GO111MODULE=on && \
    go env -w GOPROXY="https://goproxy.io,direct"

RUN go install github.com/bufbuild/buf/cmd/buf@latest \
      && go install google.golang.org/protobuf/cmd/protoc-gen-go@latest \
      && go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest \
      && go install github.com/envoyproxy/protoc-gen-validate@latest \
      && go install github.com/onsi/ginkgo/v2/ginkgo@latest \
      && go install github.com/boumenot/gocover-cobertura@latest

