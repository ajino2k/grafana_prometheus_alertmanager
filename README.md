# grafana_prometheus_alertmanager

1. The build for the Grafana docker images.
start your container binding the external port 3000

```docker run -dit -p 0.0.0.0:3000:3000 -v /data/grafana:/var/lib/grafana --name=granfana grafana/grafana```

Env Grafana : 
```
"PATH=/usr/share/grafana/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
"GF_PATHS_CONFIG=/etc/grafana/grafana.ini",
"GF_PATHS_DATA=/var/lib/grafana",
"GF_PATHS_HOME=/usr/share/grafana",
"GF_PATHS_LOGS=/var/log/grafana",
"GF_PATHS_PLUGINS=/var/lib/grafana/plugins",
"GF_PATHS_PROVISIONING=/etc/grafana/provisioning"
```




