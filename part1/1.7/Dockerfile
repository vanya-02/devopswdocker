FROM ubuntu:16.04
RUN apt-get update && apt-get install -y curl
WORKDIR /mydir
COPY script .
CMD . ./script
