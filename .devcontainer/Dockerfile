FROM ubuntu:22.04

# Install base tools and dependencies
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    curl \
    git \
    build-essential \
    libgtk-3-0 \
    libxrender1 \
    libxtst6 \
    libfontconfig1 \
    libxi6 \
    && apt-get clean

# Install Go
RUN curl -fsSL https://dl.google.com/go/go1.20.5.linux-amd64.tar.gz | tar -C /usr/local -xzf -
ENV GOROOT=/usr/local/go
ENV GOPATH=/home/dev/go
ENV PATH=$GOROOT/bin:$GOPATH/bin:$PATH

# Create a non-root user
RUN useradd -m -s /bin/bash dev && mkdir -p /workspace && chown -R dev:dev /workspace
USER dev

WORKDIR /workspace
