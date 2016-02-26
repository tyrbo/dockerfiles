FROM tyrbo/initial:latest
MAINTAINER Jonmichael Chambers <jon@tyrbo.net>

USER root

RUN apt-get update && apt-get install -y \
  bison \
  build-essential \
  flex \
  g++ \
  git \
  gperf \
  libxext-dev \
  libfontconfig1-dev \
  libfreetype6 \
  libicu-dev \
  libjpeg-dev \
  libpng-dev \
  libsqlite3-dev \
  libssl-dev \
  libx11-dev \
  perl \
  python \
  ruby \
&& rm -rf /var/lib/apt/lists/*

WORKDIR /root
RUN git clone git://github.com/ariya/phantomjs.git && \
  cd phantomjs && \
  git checkout 2.1.1 && \
  git submodule init && \
  git submodule update

RUN cd phantomjs && python build.py
RUN cp /root/phantomjs/bin/phantomjs /usr/local/bin && \
  rm -rf /root/phantomjs

USER app
WORKDIR /home/app

EXPOSE 8910

CMD ["/usr/local/bin/phantomjs", "--wd"]
