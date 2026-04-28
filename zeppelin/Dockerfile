FROM apache/zeppelin:0.12.0

USER root

RUN apt-get update && apt-get install -y wget curl && rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install -y python3 python3-pip python3-dev && \
    ln -s /usr/bin/python3 /usr/bin/python && \
    rm -rf /var/lib/apt/lists/*

ENV SPARK_VERSION=3.4.1
ENV HADOOP_VERSION=3
ENV SPARK_PACKAGE=spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}

RUN wget -q https://archive.apache.org/dist/spark/spark-${SPARK_VERSION}/${SPARK_PACKAGE}.tgz -O /tmp/spark.tgz && \
    tar -xzf /tmp/spark.tgz -C /opt/ && \
    ln -s /opt/${SPARK_PACKAGE} /opt/spark && \
    rm /tmp/spark.tgz

ENV SPARK_HOME=/opt/spark
ENV PATH=$PATH:$SPARK_HOME/bin
ENV HADOOP_CONF_DIR=/opt/spark/conf/hadoop-conf

EXPOSE 8080
CMD ["/opt/zeppelin/bin/zeppelin.sh"]