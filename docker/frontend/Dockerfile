FROM nginx

RUN rm /etc/nginx/conf.d/default.conf
COPY frontend  /usr/share/nginx/frontend
COPY docker/frontend/twasr.conf /etc/nginx/conf.d/
COPY docker/frontend/*.pem /etc/nginx/certs/
