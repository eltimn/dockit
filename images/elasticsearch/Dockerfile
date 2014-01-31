FROM dockit/openjdk7

ENV ES_VERSION 0.90.8

ADD https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-$ES_VERSION.tar.gz /elasticsearch-$ES_VERSION.tar.gz
RUN tar -zxvf elasticsearch-$ES_VERSION.tar.gz
RUN mv elasticsearch-$ES_VERSION elasticsearch

VOLUME ["/elasticsearch/data"]

ENTRYPOINT ["/elasticsearch/bin/elasticsearch", "-f"]
