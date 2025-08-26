
## Grafana Docker Configuration

```
## docker-compose.yml

services:
  grafana:
    image: grafana/grafana
    container_name: grafana
    ports:
      - "8082:3000"
    volumes:
      - ./grafana-data:/var/lib/grafana
    environment:
      - GF_SECURITY_ADMIN_USER=${GF_SECURITY_ADMIN_USER}
      - GF_SECURITY_ADMIN_PASSWORD=${GF_SECURITY_ADMIN_PASSWORD}
    restart: unless-stopped

    networks:
      - my_shared_network

networks:
  my_shared_network:
    external: true

```

```
## .env

GF_SECURITY_ADMIN_USER=nathan
GF_SECURITY_ADMIN_PASSWORD=lH1"GrZUw%6|
```


## Grafana UI configuration


```
## QUERY LANGUAGE
Flux


## URL
http://influxdb:8086 

```

```
## ORGANISATION
Orange

## TOKEN
nathan's Token (cloned at 2025-07-30 15:24:32)

## DEFAULT BUCKET
influx_data # DOCKER_INFLUXDB_INIT_BUCKET
```

