FROM nginx:1.10

ADD vhosts/nette.dev.conf /etc/nginx/conf.d/nette.dev.conf

ENV TZ=Europe/Prague
RUN echo $TZ > /etc/timezone
