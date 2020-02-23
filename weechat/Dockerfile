FROM debian:latest
RUN apt-get update\
    && apt-get -y upgrade
RUN apt-get update\
    && apt-get -y install git weechat python-pip
RUN pip install websocket-client

ENV LANG C.UTF-8
ENV HOME /weechat

RUN mkdir -p $HOME/.weechat\
    && addgroup gweechat\
    && adduser --home $HOME --shell /bin/bash weechat\
    && adduser weechat gweechat\
    && chown -R weechat:gweechat $HOME
USER weechat
VOLUME /weechat/.weechat
EXPOSE 9001
CMD ["weechat"]

