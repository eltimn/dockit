FROM dockit/elasticsearch

ENV ES_MAPPER_VERSION 1.9.0
ENV ES_MONGO_VERSION 1.7.3

RUN /elasticsearch/bin/plugin --install elasticsearch/elasticsearch-mapper-attachments/$ES_MAPPER_VERSION
RUN /elasticsearch/bin/plugin --install com.github.richardwilly98.elasticsearch/elasticsearch-river-mongodb/$ES_MONGO_VERSION
