FROM java:openjdk-8-jre
RUN apt-get update && \
    apt-get install -y dnsutils wget zookeeper && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get clean
EXPOSE 2181
CMD ["/usr/share/zookeeper/bin/zkServer.sh", "start-foreground"]
