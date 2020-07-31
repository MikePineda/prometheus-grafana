# Descripción

Este es un docker-compose que te instala los siguientes servicios/imagenes:

* Prometheus(prometheus/prometheus )

* Grafana (grafana/grafana )

* cAdvisor (Container advisor, metricas de contenedores) (google/cadvisor )

  * Redis (necesario para cAdvisor)

* Docker-host para poder acceder a puertos de tu maquina local (qoomon/docker-host )

* Node-exporter (prometheus/node_exporter )

* Apache-exporter (solsson/prometheus-exporter-apache )


Todos los exporters son opcionales, son los que llegué a necesitar en mi caso, se pueden eliminar o agregar más dependiendo de sus necesidades.

# Correr las instancias

  USER_ID=$(id -u) docker-compose up -d

# Configuración extra

* Apache: Permitir conexión a http://localhost/server-status?auto. Puedes definirlo en otro puerto si gustas pero es necesario poder acceder a esta información para el apache-exporter

https://httpd.apache.org/docs/trunk/es/mod/mod_status.html

* Docker: Definir correctamente los volumenes dependiendo de tu caso (revisar docker-compose.yml para ver volumenes, si lo deseas los puedes eliminar)

* Prometheus: Crear prometheus.yml que apunta al volumen de prometheus (se anexa ejemplo en este repositorio)

* Grafana: Las credenciales iniciales para acceder son: admin/admin

* Grafana: Una vez se acceda a la instancia solo faltará agregar el “data source”, que vendría siendo prometheus para ya comenzar a gráficar. En mi caso el url al data source es: prometheus:9000
