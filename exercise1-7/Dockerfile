FROM ubuntu:16.04 

WORKDIR /ex1_7
RUN apt-get update && apt-get install -y curl

COPY script.sh .

CMD ["bash", "script.sh"]
