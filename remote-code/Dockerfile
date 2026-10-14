FROM debian:bookworm

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    tar \
    unzip \
    git \
    && rm -rf /var/lib/apt/lists/*

# install opencode (happier) non-interactively
ENV HAPPIER_NONINTERACTIVE=1
RUN curl -fsSL https://happier.dev/install | bash

ENV PATH="/root/.local/bin:${PATH}"

WORKDIR /workspace

CMD ["sleep", "infinity"]