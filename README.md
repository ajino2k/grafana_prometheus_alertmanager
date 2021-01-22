# grafana_prometheus_alertmanager

1. The build for the Grafana docker images.
start your container binding the external port 3000

```docker run -dit -p 0.0.0.0:3000:3000 -v /data/grafana:/data/grafana --name=granfana grafana/grafana```




