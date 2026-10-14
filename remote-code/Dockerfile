FROM debian:bookworm

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    tar \
    unzip \
    git \
    && rm -rf /var/lib/apt/lists/*

# install happier non-interactively
ENV HAPPIER_NONINTERACTIVE=1
RUN curl -fsSL https://happier.dev/install | bash

# install opencode
RUN curl -fsSL https://opencode.ai/install | bash

ENV PATH="/root/.local/bin:/root/.opencode/bin:${PATH}"

# opencode config pointing at the ollama service (global config)
COPY opencode.json /root/.config/opencode/opencode.json

ENV OLLAMA_CONTEXT_LENGTH=1048576

WORKDIR /workspace

CMD ["sleep", "infinity"]