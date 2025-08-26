## Subscription

gNMIc subscribe to ``/system/memory/state/physical`` in every *10 seconds* and receive updates like : 

```
{
  "path": "/system/memory/state/physical",
  "values": {
    "in-octets": 102400,
    "out-octets": 87500
  },
  "timestamp": 1723450600000000000
}

```


## InfluxDB : gNMIc output

gNMIc transform receive updates in **influxDB points** (line protocol), example :

```
sub1,path=/system/memory/state/physical,target=leaf1 in-octets=102400i,out-octets=87500i 1723450600000000000
```

``sub1`` = subscription name = measurements influxDB
``target=leaf1`` = SRL source


Next it send via HTTP POST request to : 

```
http://clab-lab13-influxdb:8086/write?db=telemetry
Authorization: Basic gnmic:gnmic
```
