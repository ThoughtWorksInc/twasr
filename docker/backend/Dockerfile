FROM jcsilva/docker-kaldi-gstreamer-server
MAINTAINER Tong Da <tongda@outlook.com>

RUN sed -i 's/app.listen(options.port)/http_server = tornado.httpserver.HTTPServer(app, ssl_options={"certfile": options.cert_file, "keyfile": options.key_file,}); http_server.listen(options.port)/g' /opt/kaldi-gstreamer-server/kaldigstserver/master_server.py
RUN sed -i 's/define("port", default=8888, help="run on the given port", type=int)/define("port", default=8888, help="run on the given port", type=int)\ndefine("cert-file", help="https cert file path", type=str)\ndefine("key-file", help="https key file path", type=str)/g' /opt/kaldi-gstreamer-server/kaldigstserver/settings.py
RUN sed -i 's/master_server.py --port=$PORT/master_server.py --port=$PORT --cert-file=\/opt\/cert.pem --key-file=\/opt\/key.pem/g' /opt/start.sh
RUN sed -i 's/ws:\/\//wss:\/\//g' /opt/start.sh
RUN sed -i 's/import tornado.concurrent/import tornado.concurrent\nimport tornado.httpserver/g' /opt/kaldi-gstreamer-server/kaldigstserver/master_server.py

COPY docker/backend/*.pem /opt/

CMD /opt/start.sh -y /opt/models/chinese_nnet2.yaml && sleep 1 && tail -f /opt/master.log