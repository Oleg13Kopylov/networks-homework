FROM ubuntu

WORKDIR /usr/src/app

RUN apt-get update -y
RUN apt-get install -y iputils-ping

COPY ./app .

ENTRYPOINT ["bash", "Kopylov_Oleg_script_for_MTU"]
