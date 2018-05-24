FROM envoyproxy/envoy:latest as proxy
RUN apt-get update
RUN apt-get -y install curl

CMD /usr/local/bin/envoy -c /etc/service-envoy.yaml --service-cluster servicemain
