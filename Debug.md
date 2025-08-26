
Error: ✗ *provisioning.ProvisioningServiceImpl run error: Datasource provisioning error: open /etc/grafana/provisioning/datasources/datasource.yaml: permission denied

## Upgrade permission

``chmod 777 datasource.yaml``


docker logs -f gnmic 

```
2025/08/01 13:01:07.080109 [docker_loader] building target from container ["/CE3_7"]
2025/08/01 13:01:07.096868 [gnmic] failed to initialize target "R1_7": 198.18.7.1:57400: context deadline exceeded

```



Modification du mdp R1_7

login : ``admin``
password : ``nathan35``

# after week-end

## Adding configuration on nokia

```
/configure system grpc
    admin-state enable
    allow-unsecure-connection
    gnmi {
        admin-state enable
    }
    rib-api {
        admin-state enable
    }


/configure system security aaa local-profiles profile "grpc"
                grpc {
                    rpc-authorization {
                        gnmi-capabilities permit
                        gnmi-get permit
                        gnmi-set permit
                        gnmi-subscribe permit
                        rib-api-getversion permit
                        rib-api-modify permit
                    }
                }
                entry 1 {
                    action permit
                    match "configure"
                }

/configure system security user-params local-user user "admin"
                access {
                    grpc true
                }
                console {
                    member ["grpc"]
                }


```

[gnmic] failed to initialize target "R1_7": 198.18.7.1:57400: context deadline exceeded


## Adding yang-module + nokia-modules


```

/configure/system/management-interface

				yang-modules {
			        openconfig-modules true
			        nokia-combined-modules true
    }



```

## Changing paths subscriptions

- /system/memory/state/physical

## Level up permission 

 chmod +x gnmic.yaml

FAILED

## Adding SROS Nokia to the influxdb.clab.yml


## Debug en testant la connexion en mode 'skip-verify'


``docker exec clab-lab13-gnmic /app/gnmic -a 172.100.20.5:57400 -u admin -p nathan35 --skip-verify --timeout 30s --log --debug capabilities``

Reponse : 

``transport: authentication handshake failed: tls: first record does not look like a TLS handshake``


## Debug en testant la connexion en mode 'insecure'

``docker exec clab-lab13-gnmic /app/gnmic -a 172.100.20.5:57400 -u admin -p nathan35 --insecure --timeout 30s capabilities``

Reponse : 


```
gNMI version: 0.7.0 supported models:

- nokia-conf, Nokia, 22.10.R6
- nokia-state, Nokia, 22.10.R6
- nokia-li-state, Nokia, 22.10.R6
- nokia-sr-openconfig-aaa-augments, Nokia, 22.10.R6
- nokia-sr-openconfig-dev-examples-augments, Nokia, 22.10.R6
- nokia-sr-openconfig-if-ethernet-augments, Nokia, 22.10.R6
- nokia-sr-openconfig-if-ip-augments, Nokia, 22.10.R6
- nokia-sr-openconfig-mpls-augments, Nokia, 22.10.R6
- nokia-sr-openconfig-network-instance-augments, Nokia, 22.10.R6
- nokia-sr-openconfig-transport-types-augments, Nokia, 22.10.R6
- openconfig-aaa, OpenConfig working group, 0.4.0
- openconfig-aaa-types, OpenConfig working group, 0.4.0
- openconfig-acl, OpenConfig working group, 1.0.0
- openconfig-aft, OpenConfig working group, 0.2.1
- openconfig-aft-types, OpenConfig working group, 0.2.1
- openconfig-alarm-types, OpenConfig working group, 0.2.0
- openconfig-alarms, OpenConfig working group, 0.3.0
- openconfig-bfd, OpenConfig working group, 0.1.0
- openconfig-bgp, OpenConfig working group, 3.0.1
- openconfig-bgp-policy, OpenConfig working group, 4.0.1
- openconfig-bgp-types, OpenConfig working group, 3.0.1
- openconfig-dev-examples, OpenConfig working group, 1.0.0
- openconfig-dev-examples-derived-identities, OpenConfig working group, 1.0.0
- openconfig-dev-examples-identities, OpenConfig working group, 1.0.0
- openconfig-evpn, OpenConfig working group, 0.3.0
- openconfig-evpn-types, OpenConfig working group, 0.2.0
- openconfig-extensions, OpenConfig working group,
- openconfig-if-aggregate, OpenConfig working group, 2.0.0
- openconfig-if-ethernet, OpenConfig working group, 2.0.0
- openconfig-if-ip, OpenConfig working group, 2.0.0
- openconfig-if-ip-ext, OpenConfig working group, 2.0.0
- openconfig-if-types, OpenConfig working group, 0.1.0
- openconfig-igmp, OpenConfig working group, 0.2.0
- openconfig-igmp-types, OpenConfig working group, 0.1.1
- openconfig-inet-types, OpenConfig working group, 0.3.1
- openconfig-interfaces, OpenConfig working group, 2.0.0
- openconfig-isis, OpenConfig working group, 0.3.2
- openconfig-isis-lsdb-types, OpenConfig working group, 0.3.2
- openconfig-isis-policy, OpenConfig working group, 0.3.2
- openconfig-isis-types, OpenConfig working group, 0.3.2
- openconfig-lacp, OpenConfig working group, 1.1.0
- openconfig-license, OpenConfig working group, 0.2.0
- openconfig-lldp, OpenConfig working group, 0.1.0
- openconfig-lldp-types, OpenConfig working group, 0.1.0
- openconfig-local-routing, OpenConfig working group, 1.0.1
- openconfig-messages, OpenConfig working group, 0.0.1
- openconfig-mpls, OpenConfig working group, 2.3.0
- openconfig-mpls-ldp, OpenConfig working group, 3.0.2
- openconfig-mpls-rsvp, OpenConfig working group, 2.3.0
- openconfig-mpls-sr, OpenConfig working group, 2.3.0
- openconfig-mpls-types, OpenConfig working group, 2.3.0
- openconfig-network-instance, OpenConfig working group, 1.1.0
- openconfig-network-instance-l3, OpenConfig working group, 0.11.1
- openconfig-network-instance-types, OpenConfig working group, 0.9.3
- openconfig-ospf-types, OpenConfig working group, 0.1.0
- openconfig-ospfv2, OpenConfig working group, 0.1.0
- openconfig-packet-match, OpenConfig working group, 1.0.0
- openconfig-packet-match-types, OpenConfig working group, 1.0.0
- openconfig-pim, OpenConfig working group, 0.2.0
- openconfig-pim-types, OpenConfig working group, 0.1.1
- openconfig-platform, OpenConfig working group, 0.12.2
- openconfig-platform-fan, OpenConfig working group, 0.1.1
- openconfig-platform-linecard, OpenConfig working group, 0.1.2
- openconfig-platform-port, OpenConfig working group, 0.3.3
- openconfig-platform-transceiver, OpenConfig working group, 0.7.1
- openconfig-platform-types, OpenConfig working group, 1.0.0
- openconfig-policy-forwarding, OpenConfig working group, 0.0.1
- openconfig-policy-types, OpenConfig working group, 3.1.0
- openconfig-procmon, OpenConfig working group, 0.4.0
- openconfig-relay-agent, OpenConfig working group, 0.1.0
- openconfig-routing-policy, OpenConfig working group, 3.0.0
- openconfig-rsvp-sr-ext, OpenConfig working group, 0.1.0
- openconfig-segment-routing, OpenConfig working group, 0.0.3
- openconfig-system, OpenConfig working group, 0.9.1
- openconfig-system-logging, OpenConfig working group, 0.3.1
- openconfig-system-management, OpenConfig working group, 0.1.1
- openconfig-system-terminal, OpenConfig working group, 0.3.0
- openconfig-telemetry, OpenConfig working group, 0.5.0
- openconfig-telemetry-types, OpenConfig working group, 0.4.1
- openconfig-terminal-device, OpenConfig working group, 1.7.3
- openconfig-transport-types, OpenConfig working group, 0.12.0
- openconfig-types, OpenConfig working group, 0.5.0
- openconfig-vlan, OpenConfig working group, 2.0.0
- openconfig-vlan-types, OpenConfig working group, 2.0.0
- openconfig-yang-types, OpenConfig working group, 0.2.0
- nokia-sr-openconfig-acl-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-alarms-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-bfd-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-bgp-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-bgp-policy-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-if-aggregate-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-if-ethernet-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-if-ip-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-if-ip-ext-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-igmp-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-interfaces-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-isis-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-isis-policy-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-lacp-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-lldp-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-local-routing-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-messages-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-mpls-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-mpls-ldp-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-mpls-rsvp-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-network-instance-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-network-instance-l3-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-ospfv2-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-packet-match-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-pim-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-platform-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-platform-fan-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-platform-linecard-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-platform-port-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-platform-transceiver-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-relay-agent-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-routing-policy-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-rsvp-sr-ext-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-system-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-system-logging-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-system-management-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-system-terminal-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-telemetry-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-terminal-device-deviations, Nokia, 22.10.R6
- nokia-sr-openconfig-vlan-deviations, Nokia, 22.10.R6 supported encodings:
- JSON
- BYTES
- PROTO
- JSON_IETF
```


# CA FONCTIONNE !!!!!!

## Modification du paramètre connexion + de l'encodage

gnmic.yml

``insecure: true``
``encoding: json_ietf``
