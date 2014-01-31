FROM dockit/openjdk7:latest

RUN apt-get update

ENV JETTY_VERSION 9.1.0.v20131115
ADD jetty-distribution-$JETTY_VERSION.tar.gz /jetty-distribution-$JETTY_VERSION.tar.gz
RUN tar -zxvf jetty-distribution-$JETTY_VERSION.tar.gz
RUN mv jetty-distribution-$JETTY_VERSION jetty
RUN rm jetty-distribution-$JETTY_VERSION.tar.gz

RUN apt-get -y upgrade

CMD ["java", "$JVM_OPTS", "-Djetty.home=/jetty", "-jar", "/jetty/start.jar", "jetty.base=/jetty/demo-base"]

#docker run -name testjt8 -t -i dockit/jetty8 bash
