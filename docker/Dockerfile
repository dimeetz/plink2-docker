FROM ubuntu:22.04 AS unzip
ENV download=https://s3.amazonaws.com/plink2-assets/plink2_linux_x86_64_20250920.zip
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y curl unzip
RUN curl -L "${download}" --output /tmp/plink2.zip
RUN unzip /tmp/plink2.zip -d /tmp

FROM ubuntu:22.04
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y bash coreutils && \
    rm -rf /var/lib/apt/lists/*
COPY --from=unzip /tmp/plink2 /usr/local/bin/plink2
RUN chmod +x /usr/local/bin/plink2
