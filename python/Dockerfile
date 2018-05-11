FROM debian:latest

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /opt/conda/bin:$PATH

RUN apt-get update --fix-missing && apt-get install -y bzip2 mysql-server python-dev default-libmysqlclient-dev ca-certificates \
    libglib2.0-0 libxext6 libsm6 libxrender1 \
    git mercurial subversion


COPY data/anaconda3/Anaconda3-5.1.0-Linux-x86_64.sh /anaconda3.sh
RUN /bin/bash /anaconda3.sh -b -p /opt/conda && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    rm /anaconda3.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc

RUN apt-get install -y curl grep sed dpkg && \
    TINI_VERSION=`curl https://github.com/krallin/tini/releases/latest | grep -o "/v.*\"" | sed 's:^..\(.*\).$:\1:'` && \
    curl -L "https://github.com/krallin/tini/releases/download/v${TINI_VERSION}/tini_${TINI_VERSION}.deb" > tini.deb && \
    dpkg -i tini.deb && \
    rm tini.deb && \
    apt-get clean

#RUN conda update -n base conda && \
#    conda install -c anaconda mysql-connector-python

RUN mkdir /var/lib/python /var/lib/python/nltk && \
    pip install mysqlclient && \
    pip install django==1.11

ENTRYPOINT [ "/usr/bin/tini", "--" ]
CMD [ "/bin/bash" ]