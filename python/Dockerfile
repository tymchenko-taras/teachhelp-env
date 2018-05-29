FROM python:3
ENV PYTHONUNBUFFERED 1
RUN pip install \
    mysqlclient \
    django==1.11 \
    nltk \
    numpy \
    scikit-learn \
    pandas

RUN apt-get update && apt-get install -y openssh-server \
&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps


RUN mkdir authorized_keys /var/lib/python/nltk /var/log/python
COPY authorized_keys /root/.ssh/authorized_keys
COPY sshd_config /etc/ssh/sshd_config
