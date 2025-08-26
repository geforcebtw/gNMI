*SR Linux natively includes a gNMI server*
*It is integrated into mgmt-server, a component of SR Linux's management plane (comparable to NETCONF/RESTCONF on other operating systems)*


## Agent working : 

- Listen in gRPC/TLS on the 57400 port
- Exposed all YANG data
- Support :
  - ``Get``
  - ``Subscribe``
  - ``Set``
  - ``Capabilities``

## Authentification
That's how the authentification with the gNMIC module works : 


```
## gnmic.yaml


username: admin
password: NokiaSrl1!    ## Credentials in SR Linux
skip-verify: true       ## Not obligatory
encoding: ascii         ## Or "json-ietf"
log: true
insecure: true
timeout: 60s
```
