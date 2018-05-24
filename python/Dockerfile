FROM python:3
ENV PYTHONUNBUFFERED 1

# install ssh to connect to interpreter via pyCharm
RUN apt-get update && apt-get install -y openssh-server \
&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps


RUN mkdir authorized_keys /var/lib/python /var/lib/python/nltk /var/log/python /root/.pycharm_helpers
COPY authorized_keys /root/.ssh/authorized_keys
COPY sshd_config /etc/ssh/sshd_config
COPY requirements.txt /var/lib/python/requirements.txt

RUN pip install -r /var/lib/python/requirements.txt