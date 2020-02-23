FROM debian:latest
# Bitlbee
RUN apt-get update && apt-get -y upgrade && apt-get -y install wget gnupg
RUN bash -c "echo deb http://code.bitlbee.org/debian/master/testing/amd64/ ./ >> /etc/apt/sources.list.d/bitlbee.list"
RUN bash -c "wget -O- https://code.bitlbee.org/debian/release.key | apt-key add -"
RUN apt-get update && apt-get -y install bitlbee bitlbee-dev


# Facebook
RUN bash -c "echo deb http://download.opensuse.org/repositories/home:/jgeboski/Debian_9.0 ./ >> /etc/apt/sources.list.d/jgeboski.list"
RUN bash -c "wget -O- https://jgeboski.github.io/obs.key | apt-key add -"
RUN apt-get update && apt-get -y install bitlbee-facebook
COPY bitlbee/bitlbee.conf /etc/bitlbee/bitlbee.conf

# Discord
RUN apt-get update && apt-get -y upgrade && apt-get -y install git autotools-dev autoconf libtool libglib2.0-dev make
RUN git clone https://github.com/sm00th/bitlbee-discord.git
RUN cd bitlbee-discord && ./autogen.sh
RUN cd bitlbee-discord && ./configure
RUN cd bitlbee-discord && make
RUN cd bitlbee-discord && make install

VOLUME /var/lib/bitlbee/
EXPOSE 6667
USER bitlbee
CMD ["bitlbee", "-n"]

