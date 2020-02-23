FROM nginx:latest
RUN apt-get update\
    && apt-get -y install git
RUN cd /usr/share/nginx/\
    && git clone https://github.com/glowing-bear/glowing-bear.git\
    && mv html html.old\
    && mv glowing-bear html

COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

