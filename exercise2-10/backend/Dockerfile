FROM ubuntu:16.04 

WORKDIR /backend-example-docker

RUN apt update && apt install -y curl 
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash && apt install -y nodejs && npm install

COPY . .

RUN npm install 

ENV FRONT_URL=http://localhost/

ENTRYPOINT npm start 
