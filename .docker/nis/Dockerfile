FROM ubuntu:20.04

RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

RUN apt update
RUN apt install -y tar unzip curl git openjdk-11-jdk maven
RUN apt clean

RUN git clone https://github.com/NemProject/nem.git -b v0.6.102 nis1
WORKDIR /nis1/infra
RUN ./package.build.sh build.log
RUN ./package.prepare.sh
RUN sed -i 's/nem\.network = \r/nem.network = mainnet/g' package/nis/config.properties
RUN chmod +x package/nix.runNis.sh
RUN cp -r package /package

EXPOSE 7778
EXPOSE 7890

WORKDIR /package/nis
ENTRYPOINT [ "java", "-cp", ".:./*:../libs/*", "org.nem.deploy.CommonStarter" ]
CMD [ "-Xms4G", "-Xmx6G" ]
