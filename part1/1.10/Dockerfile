FROM ubuntu:16.04
WORKDIR /mydir
COPY frontend-example-docker/ .
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt-get install -y nodejs && npm install
EXPOSE 5000
CMD npm start
