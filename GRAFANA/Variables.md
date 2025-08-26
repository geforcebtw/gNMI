## Dashboard variables

### Variables settings



Adding some variables like 'source::tag' or 'port-id'.

- ``Grafana > Dashboards > Settings > Variables > New variable > ``
- **Variable type** : ``Query``
- **Name** : ``source              ## As you want``
- **Data source** : ``influxDB``
- **Query** : ``SHOW TAG VALUES FROM "sub" WITH KEY = "source"``
	- *For debugging* : ``docker exec influxdb influx -database 'telemetry' -execute 'SHOW TAG VALUES FROM "sub" WITH KEY = "source"'``
- **Sort** : ``As you want``


##### Dashboard query

- **Select** : ``raw query mode     ## that prevent regex syntax``

- **Query** : ``SELECT "/state/port/oper-state" FROM "sub2" WHERE ("port_port-id"::tag = '$port' AND "source"::tag = '$source' ) AND $timeFilter``

