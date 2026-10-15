FROM debian:bookworm

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    tar \
    unzip \
    git \
    && rm -rf /var/lib/apt/lists/*

# install opencode
RUN curl -fsSL https://opencode.ai/install | bash
ENV PATH="/root/.opencode/bin:${PATH}"
COPY opencode.json /root/.config/opencode/opencode.json

WORKDIR /workspace

CMD opencode serve