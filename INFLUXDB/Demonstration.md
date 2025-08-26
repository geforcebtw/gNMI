*dir : /home/sysadmin/clabs/labs_nathan/gNMI/gnmic/examples/deployments/1.single-instance/3.influxdb-output/containerlab*

```
## DEMO

root@muztc: /dir# docker exec -it clab-lab13-influxdb influx

Connected to http://localhost:8086 version 1.8.10
InfluxDB shell version: 1.8.10

> show databases
name: databases
name
----
telemetry
_internal

> use telemetry
Using database telemetry

> show measurements
name: measurements
name
----
sub1

> select * from sub1 limit 5
...
```

