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

2. Build Prometheus from docker images, container binding external port 9090 

```docker run -dit -p 0.0.0.0:9090:9090 -v /data/prometheus/prometheus.yml:/etc/prometheus/prometheus.yml --name=prometheus prometheus```


Evn Prometheus :
```
"--config.file=/etc/prometheus/prometheus.yml",
"--storage.tsdb.path=/prometheus",
"--web.console.libraries=/usr/share/prometheus/console_libraries",
"--web.console.templates=/usr/share/prometheus/consoles"
```

3. Alertmanager from Docker images binding external port 9093

```docker run -dit -p 0.0.0.0:9093:9093 -v /data/alertmanager/alertmanager.yml:/etc/alertmanager/alertmanager.yml --name=alertmanager alermanager```

Env Alertmanager : 

```
"--config.file=/etc/alertmanager/alertmanager.yml",
"--storage.path=/alertmanager"
"Image": "docker.io/prom/alertmanager",
"Volumes": {
"/alertmanager": {}
"WorkingDir": "/alertmanager",
"Entrypoint": [
"/bin/alertmanager"
```

4. Setup Alertmanager send alert via microsoft Teams using proxy prometheusmsteam (Alertmanage do not support send alert via microsoft Teams)

```
docker run -d -p 10.148.0.9:2021:2000 --name="proxy-promteams" -v /prometheusmsteams/config.yml:/prometheusmsteams/config.yml -e CONFIG_FILE="/prometheusmsteams/config.yml" quay.io/prometheusmsteams/prometheus-msteams:v1.4.1
```

Env Proxy Prometheus microsoft Teams .
```
"CONFIG_FILE=/home/config.yml",
```
