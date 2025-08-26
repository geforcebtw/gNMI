## Connexion CLI

```
docker exec -it influxdb influx
```

## Commands inject

```
docker exec influxdb influx
```


```
docker exec influxdb influx -database 'telemetry' -execute 'SHOW TAG KEYS FROM "sub"'
```


## SHOW FIELDS KEYS

```
SHOW FIELD KEYS FROM "sub"
```

## SHOW TAG KEYS

```
SHOW TAG KEYS FROM "sub"
```
