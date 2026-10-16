FROM debian:bookworm

ENV DEBIAN_FRONTEND=noninteractive

# docker CLI only, the daemon runs on the host
COPY --from=docker:cli /usr/local/bin/docker /usr/local/bin/docker
COPY --from=docker:cli /usr/local/bin/docker-compose /usr/local/bin/docker-compose

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    tar \
    unzip \
    openssh-client \
    git \
    && rm -rf /var/lib/apt/lists/*

# install opencode
RUN curl -fsSL https://opencode.ai/install | bash
ENV PATH="/root/.opencode/bin:${PATH}"
COPY opencode.json /root/.config/opencode/opencode.json

WORKDIR /workspace

CMD opencode serve