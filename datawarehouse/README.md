<p align="center">
    <img src="https://image-resize-072781403939-us-east-1.s3.amazonaws.com/warehouse-logo.png" width="500">
</p>

### Local Environment

`sudo ifconfig lo0 alias 127.0.0.150 up`

`make up`
`make logs`
`make status`


### Migrating from bowtie - products

```bash
cd bowtie
docker-compose down --remove-orphans

cd products
docker-compose down --remove-orphans
```

```
make up
```

### Services

#### RabbitMQ
```
internal-name: rabbitmq
username: rabbitmq
password: secret
```
#### Elasticsearch
```
internal-name: elasticsearch
port: 9200
username: admin
password: admin
SSL OFF
```
#### Memcached
```
internal-name: memcached
port: 11211
```
#### StatsD Exporter
```
internal-name: statsd-exporter
web: http://127.0.0.150:9102/metrics
port: 9125/udp

mapping-file: ./.docker/statsd/mapping.yaml
```
#### Localstack
```
internal-name: localstack
endpoint-url: http://127.0.0.150:4566
```
#### Kibana
```
http://127.0.0.150:5601/
username: admin
password: admin
```
#### Grafana
```
http://127.0.0.150:3000/
username: admin
password: foobar
```

### Extra commands

`make export-queue-definitions` exports queues from rabbitmq to json file so they're imported automatically when new container & volume runs
