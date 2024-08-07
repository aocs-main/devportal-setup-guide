# Developer guide

This guide helps you get started customizing Developer Portal.

## Dependencies


Make sure you have the following dependencies installed before setting up your developer environment:

- [Docker](https://www.docker.com/)


## Getting started

Create a private Docker network named devportal-network:

```sh
docker network create devportal-network
```

Create elasticsearch:

```sh
docker run -d -e "discovery.type=single-node" -e "xpack.security.enabled=false" -u elasticsearch --net devportal-network --hostname devportal-elastic --name elasticsearch --net-alias devportal-elastic docker.elastic.co/elasticsearch/elasticsearch:8.2.3
```


Create Developer Portal 10.15:

```sh
docker run -d -e SPRING_ELASTICSEARCH_REST_URIS="http://devportal-elastic:9200" --net devportal-network --hostname devportal-server -p 80:8083 softwareag/devportal:10.15
```




Now you can access the Developer Portal by hitting 'http://localhost:80/portal⁠' in a browser and will be able to login with default credentials.

```
Username: Administrator
Password: manage
```


## Documentation

The documentation is available at [docs](./docs)
