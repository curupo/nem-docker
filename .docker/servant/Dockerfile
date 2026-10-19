FROM eclipse-temurin:11-jre

RUN apt update
RUN apt install -y unzip

RUN curl https://bob.nem.ninja/servant_0_0_4.zip -o servant.zip
RUN unzip servant.zip
RUN rm servant.zip
RUN chmod +x servant/startservant.sh

EXPOSE 7880

WORKDIR /servant
ENTRYPOINT [ "java", "-cp", ".:jars/*", "org.nem.rewards.servant.NodeRewardsServant" ]
CMD [ "-Xms256M", "-Xmx256M" ]
