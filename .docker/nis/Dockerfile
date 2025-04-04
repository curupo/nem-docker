FROM ubuntu:20.04

RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

RUN apt update
RUN apt install -y --no-install-recommends curl tar unzip openjdk-11-jre-headless maven git
RUN apt clean

WORKDIR /work

RUN git clone https://github.com/NemProject/nem.git -b v0.6.102 nis1
RUN cd nis1/infra && ./package.build.sh
RUN cd nis1/infra && ./package.prepare.sh
RUN chmod +x package/nix.runNis.sh

EXPOSE 7778
EXPOSE 7890

WORKDIR /work/package/nis
ENTRYPOINT [ "java", "-cp", ".:./*:../libs/*", "org.nem.deploy.CommonStarter" ]
CMD [ "-Xms4G", "-Xmx6G" ]

