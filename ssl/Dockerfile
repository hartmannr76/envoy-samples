FROM envoyproxy/envoy:latest as proxy
RUN apt-get update

FROM microsoft/aspnetcore-build:2.0
COPY --from=proxy /usr/local/bin/envoy /usr/local/bin/envoy

ENV ASPNETCORE_URLS http://*:8080
WORKDIR /app

RUN dotnet new webapi
RUN dotnet restore
RUN dotnet publish -o ./publish

CMD dotnet ./publish/app.dll & /usr/local/bin/envoy -c /etc/service-envoy.yaml --service-cluster servicemain
