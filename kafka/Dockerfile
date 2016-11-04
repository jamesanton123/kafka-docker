FROM java:openjdk-8-jre

ENV DEBIAN_FRONTEND noninteractive
ENV SCALA_VERSION 2.11
ENV KAFKA_VERSION 0.10.1.0
ENV KAFKA_HOME /opt/kafka_"$SCALA_VERSION"-"$KAFKA_VERSION"

RUN apt-get update && apt-get install -y \
  dnsutils \
  wget && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get clean
	
RUN wget -q http://apache.mirrors.spacedump.net/kafka/"$KAFKA_VERSION"/kafka_"$SCALA_VERSION"-"$KAFKA_VERSION".tgz -O /tmp/kafka_"$SCALA_VERSION"-"$KAFKA_VERSION".tgz && \
    tar xfz /tmp/kafka_"$SCALA_VERSION"-"$KAFKA_VERSION".tgz -C /opt && \
    rm /tmp/kafka_"$SCALA_VERSION"-"$KAFKA_VERSION".tgz
	
#This line forces everything above to be cached, and everything below to be rebuilt
ENV updated-adds-on 14-DEC-14

ADD conf/server.properties /opt/kafka_"$SCALA_VERSION"-"$KAFKA_VERSION"/config/
RUN chmod 777 /opt/kafka_"$SCALA_VERSION"-"$KAFKA_VERSION"/config/server.properties

EXPOSE 9092

CMD ["/opt/kafka_2.11-0.10.1.0/bin/kafka-server-start.sh", "/opt/kafka_2.11-0.10.1.0/config/server.properties"]