FROM ubuntu:latest

RUN apt-get update && apt-get install -y \
    ca-certificates \
    curl \
    wget \
    gnupg \
    iputils-ping \
    lsb-release \
    pass \
    faketime \
    sudo \
    && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null \
    && apt-get update \
    && apt-get install -y docker-ce-cli

RUN echo "ubuntu ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
# install envx
RUN curl -sfS https://dotenvx.sh | sh
COPY bin/* /usr/local/bin/
