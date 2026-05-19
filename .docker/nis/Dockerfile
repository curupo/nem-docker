FROM ubuntu:26.04

RUN apt update
RUN apt install -y tar curl openjdk-11-jre-headless
RUN apt clean

RUN curl -L https://github.com/NemProject/nem/releases/download/v0.6.102/nis-0.6.102.tgz -o nis-0.6.102.tgz
RUN tar -zxvf nis-0.6.102.tgz
RUN rm nis-0.6.102.tgz

RUN chmod +x package/nix.runNis.sh

EXPOSE 7778
EXPOSE 7890

WORKDIR /package/nis
ENTRYPOINT [ "java", "-cp", ".:./*:../libs/*", "org.nem.deploy.CommonStarter" ]
CMD [ "-Xms4G", "-Xmx4G" ]
