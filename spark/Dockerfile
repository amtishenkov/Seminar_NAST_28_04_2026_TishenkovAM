FROM apache/spark:3.4.1

USER root

RUN apt-get update && apt-get install -y python3.9 python3.9-dev python3-pip curl && \
    ln -sf /usr/bin/python3.9 /usr/bin/python3 && \
    ln -sf /usr/bin/python3.9 /usr/bin/python && \
    rm -rf /var/lib/apt/lists/*

RUN mkdir -p /opt/conda/envs/python_3_with_R/bin && \
    ln -sf /usr/bin/python3.9 /opt/conda/envs/python_3_with_R/bin/python

USER spark