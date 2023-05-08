FROM --platform=linux/amd64 node:18
RUN curl -fsSL https://sdk.dfinity.org/install.sh | sh
RUN chmod +x /usr/local/bin/dfx
RUN apt-get update && apt-get install -y libunwind-dev && rm -rf /var/lib/apt/lists/*
