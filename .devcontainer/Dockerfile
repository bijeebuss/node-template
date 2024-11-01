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
    xz-utils \
    && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null \
    && apt-get update \
    && apt-get install -y docker-ce-cli

RUN echo "ubuntu ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
# install envx
RUN curl -sfS https://dotenvx.sh | sh

# install node
RUN wget https://nodejs.org/dist/v22.11.0/node-v22.11.0-linux-x64.tar.xz
RUN tar -xf node-v22.11.0-linux-x64.tar.xz
RUN mv node-v22.11.0-linux-x64 /usr/local/node
RUN ln -s /usr/local/node/bin/node /usr/local/bin/node
RUN ln -s /usr/local/node/bin/npm /usr/local/bin/npm
RUN ln -s /usr/local/node/bin/npx /usr/local/bin/npx
RUN rm node-v22.11.0-linux-x64.tar.xz

COPY bin/* /usr/local/bin/
