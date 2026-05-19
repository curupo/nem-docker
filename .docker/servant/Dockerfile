FROM ubuntu:26.04

RUN apt update
RUN apt install -y --no-install-recommends curl unzip openjdk-11-jre-headless
RUN apt clean

WORKDIR /work

RUN curl https://bob.nem.ninja/servant_0_0_4.zip -o servant.zip
RUN unzip servant.zip
RUN rm servant.zip
RUN chmod +x servant/startservant.sh

EXPOSE 7880

WORKDIR /work/servant
ENTRYPOINT [ "java", "-cp", ".:jars/*", "org.nem.rewards.servant.NodeRewardsServant" ]
CMD [ "-Xms256M", "-Xmx256M" ]

