FROM ubuntu:16.04

RUN apt-get update \
    && apt-get -y install \
        sphinxsearch=2.2.9-1build1 \
        wget \
    && rm -r /var/lib/apt/lists/*


COPY start.sh /start.sh
RUN chmod +x /start.sh

VOLUME ["/usr/local/etc"]
VOLUME ["/usr/local/var/data"]

EXPOSE 9312 9306

CMD ["/start.sh"]
