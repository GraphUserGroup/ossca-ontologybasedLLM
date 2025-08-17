FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

# 1. install required packages
RUN apt-get update && apt-get install -y \
    curl ca-certificates gnupg lsb-release unzip software-properties-common \
    python3 python3-pip python3-venv docker.io

# 2. install Docker Compose v2
RUN mkdir -p /usr/libexec/docker/cli-plugins && \
    curl -SL https://github.com/docker/compose/releases/download/v2.24.5/docker-compose-linux-$(uname -m) -o /usr/libexec/docker/cli-plugins/docker-compose && \
    chmod +x /usr/libexec/docker/cli-plugins/docker-compose

# 3. install datahub cli
RUN pip install --upgrade pip && \
    pip install acryl-datahub

# 4. working directory
WORKDIR /workspace

# 5. directly run datahub docker quickstart
CMD ["datahub", "docker", "quickstart"]