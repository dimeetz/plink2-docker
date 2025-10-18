FROM ubuntu AS unzip

ENV download=https://s3.amazonaws.com/plink2-assets/plink2_linux_x86_64_20250920.zip
RUN apt-get update 
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y curl unzip
RUN curl ${download}  --output plink2.zip
RUN unzip plink2.zip

FROM ubuntu
COPY --from=unzip plink2 /usr/bin/plink2

CMD ["/usr/bin/plink2", "--help"]