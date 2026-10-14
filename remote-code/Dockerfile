FROM debian:bookworm

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    tar \
    unzip \
    git \
    && rm -rf /var/lib/apt/lists/*

# install happier non-interactively. Binaries go to /opt/happier so the
# /root/.happier volume mount only holds data (auth/session), not the binary.
ENV HAPPIER_NONINTERACTIVE=1 \
    HAPPIER_INSTALL_DIR=/opt/happier \
    HAPPIER_NO_PATH_UPDATE=1
RUN curl -fsSL https://happier.dev/install | bash 
    # strip any HAPPIER exports the installer wrote to rc files — PATH comes
    # from the image ENV, and HAPPIER_HOME_DIR must stay at /root/.happier
    #&& sed -i '/HAPPIER/d' /root/.bashrc /root/.profile 2>/dev/null || true

# install opencode
RUN curl -fsSL https://opencode.ai/install | bash

ENV PATH="/opt/happier/bin:/root/.opencode/bin:${PATH}"

# opencode config pointing at the ollama service (global config)
COPY opencode.json /root/.config/opencode/opencode.json

ENV OLLAMA_CONTEXT_LENGTH=1048576

WORKDIR /workspace

CMD happier opencode || sleep infinity