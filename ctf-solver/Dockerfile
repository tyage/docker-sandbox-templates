# Final stage
FROM docker/sandbox-templates:gemini

USER root

# Install runtime dependencies (minimal)
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    gdb \
    ltrace \
    strace \
    netcat-openbsd \
    socat \
    curl \
    wget \
    nmap \
    vim \
    nano \
    git \
    file \
    unzip \
    libssl-dev \
    libffi-dev \
    python3-pip \
    python3-venv \
    python3-dev \
    binutils \
    checksec \
    gdbserver \
    ncurses-term \
    && rm -rf /var/lib/apt/lists/*

# Install Python tools
RUN pip3 install --no-cache-dir --break-system-packages \
    pwntools \
    requests \
    scapy \
    angr \
    openai \
    anthropic

# Install GEF for GDB
RUN wget -O ~/.gdbinit-gef.py -q https://gef.blah.cat/py && \
    echo source ~/.gdbinit-gef.py >> ~/.gdbinit && \
    cp ~/.gdbinit /home/agent/.gdbinit && \
    chown agent:agent /home/agent/.gdbinit

ENV TERM=xterm

USER agent
