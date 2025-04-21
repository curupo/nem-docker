FROM ubuntu:20.04

RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

RUN apt update
RUN apt install -y tar unzip curl git openjdk-11-jre-headless
RUN apt clean

RUN curl -L https://github.com/NemProject/nem/releases/download/v0.6.102/nis-0.6.102.tgz -o nis-0.6.102.tgz
RUN tar -zxvf nis-0.6.102.tgz
RUN rm nis-0.6.102.tgz

RUN chmod +x package/nix.runNis.sh

EXPOSE 7778
EXPOSE 7890

WORKDIR /package/nis
ENTRYPOINT [ "java", "-cp", ".:./*:../libs/*", "org.nem.deploy.CommonStarter" ]
CMD [ "-Xms4G", "-Xmx6G" ]
