FROM dockit/base

#ENV RABBITMQ_VERSION 3.2.2-1

ADD http://www.rabbitmq.com/rabbitmq-signing-key-public.asc /rabbitmq-signing-key-public.asc
RUN apt-key add rabbitmq-signing-key-public.asc
RUN echo "deb http://www.rabbitmq.com/debian/ testing main" > /etc/apt/sources.list.d/rabbitmq.list
RUN apt-get update
RUN apt-get -y -q install rabbitmq-server

RUN /usr/sbin/rabbitmq-plugins enable rabbitmq_management
ADD etc_default_rabbitmq /etc/default/rabbitmq-server

ENTRYPOINT ["/usr/sbin/rabbitmq-server"]
