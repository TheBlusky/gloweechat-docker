FROM nginx:latest
RUN apt-get update\
    && apt-get -y upgrade
RUN apt-get update\
    && apt-get -y install git weechat supervisor
RUN cd /usr/share/nginx/\
    && git clone https://github.com/glowing-bear/glowing-bear.git\
    && mv html html.old\
    && mv glowing-bear html

ENV LANG C.UTF-8
ENV HOME /weechat

RUN mkdir -p $HOME/.weechat\
    && addgroup gweechat\
    && adduser --home $HOME --shell /bin/bash weechat\
    && adduser weechat gweechat\
    && chown -R weechat:gweechat $HOME


COPY supervisord.conf /etc/supervisord.conf
COPY nginx.conf /etc/nginx/conf.d/default.conf


VOLUME /weechat/.weechat
EXPOSE 80
CMD ["/usr/bin/supervisord", "-n"]
