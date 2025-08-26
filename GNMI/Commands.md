## Capabilities 

```
docker exec gnmic /app/gnmic -a @:57400 -u admin -p nathan35 --insecure --timeout 30s capabilities
```

## Statistics [port-id=x/x/x]

```
docker exec gnmic /app/gnmic -a 198.18.7.1:57400 -u admin -p nathan35 --insecure get --path /state/port[port-id=1/1/1]/statistics --encoding json_ietf
```


## Oper-state ports

```
docker exec gnmic /app/gnmic -a 198.18.7.1:57400 -u admin -p nathan35 --insecure get --path /state/port/oper-state --encoding json_ietf

```
