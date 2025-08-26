*You can find all the official documentation here : https://github.com/openconfig/gnmic*


## What is gNMI ? (gRPC Network Management Interface)

Is an open telemetry protocol defined by openconfig that permit to question and subscribe to YANG paths.
Some YANG paths examples : 
  -  ``/interfaces/interface/state/counters``
  -  ``/network-instances/network-instance/protocols/protocol/bgp``
gNMI works on gRPC with TLS encryption.

SR LINUX are the Data source and played the role of gNMIC target (server).


## What is gNMIC ? (gRPC Network Management Interface Client)

- It's a client that automatically discovered SR Linux (over Docker labels with loader.docker)
- Establish secured gNMI session with every SRL (SR Linux)
- Subscribe to YANG path defined in 'subscriptions:' sections.
- Push the data to the output - here InfluxDB



## How to instantiate them ? 

In the yaml topology of containerlab. (refer to the ``/containerlab/influxdb.clab.yaml`` && ``/containerlab/gnmic.yaml`` for full details)

SR Linux : 

```
kinds:
    srl:
      image: ghcr.io/nokia/srlinux

  nodes:
    spine1:
    spine2:
    leaf1:
    leaf2:
    leaf3:
    leaf4:
```

gNMIC : 

```
gnmic:
      kind: linux
      mgmt-ipv4: x.x.x.x/xx
      image: docker-proxy-asis-ghcr.repos.tech.orange/openconfig/gnmic:0.34.2
      binds:
        - ./gnmic.yaml:/app/gnmic.yaml:ro
        - /var/run/docker.sock:/var/run/docker.sock
      cmd: '--config /app/gnmic.yaml --log subscribe'

```
