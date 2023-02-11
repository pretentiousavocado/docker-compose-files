  #other
  # homer:
  #   image: b4bz/homer
  #   container_name: homer
  #   environment:
  #     - UID=1000
  #     - GID=1000
  #   labels:
  #     - traefik.enable=true
  #     - traefik.docker.network=backend # (internal only network for traefik.)
  #     - traefik.http.routers.homer-http.rule=Host(`homer.example.com`)
  #     - traefik.http.routers.homer-http.entrypoints=http
  #     - traefik.http.routers.homer-http.middlewares=https-redirect
  #     - traefik.http.routers.homer-https.rule=Host(`homer.example.com`)
  #     - traefik.http.routers.homer-https.entrypoints=https
  #     - traefik.http.routers.homer-https.tls=true
  #     - traefik.http.services.homer.loadbalancer.server.port=8080
  #     - traefik.http.services.homer.loadbalancer.server.scheme=http
  #   volumes:
  #     - homer:/www/assets
  #   networks:
  #     - backend # (internal only network for traefik.)
  #   restart: unless-stopped

  # loki:
  #   container_name: loki
  #   image: grafana/loki:latest
  #   volumes:
  #     - /opt/docker-data/loki:/etc/loki
  #   # ports:
  #   #   - "3100:3100"
  #   labels:
  #     - traefik.enable=true
  #     - traefik.docker.network=backend # (internal only network for traefik.)
  #     - traefik.http.routers.loki-http.rule=Host(`loki.example.com`)
  #     - traefik.http.routers.loki-http.entrypoints=http
  #     - traefik.http.routers.loki-http.middlewares=https-redirect
  #     - traefik.http.routers.loki-https.rule=Host(`loki.example.com`)
  #     - traefik.http.routers.loki-https.entrypoints=https
  #     - traefik.http.routers.loki-https.tls=true
  #     - traefik.http.services.loki.loadbalancer.server.port=3100
  #     - traefik.http.services.loki.loadbalancer.server.scheme=http
  #   restart: unless-stopped
  #   command: -config.file=/etc/loki/loki-config.yml
  #   networks:
  #     - backend # (internal only network for traefik.)
  #     - vlanx # (Exposed to Internet)

  # promtail:
  #   image: grafana/promtail:main
  #   container_name: promtail
  #   volumes:
  #     - /var/log:/var/log
  #     - /opt/docker-data/promtail:/etc/promtail
  #   ports:
  #      - "1514:1514" # this is only needed if you are going to send syslogs
  #   restart: unless-stopped
  #   command: -config.file=/etc/promtail/promtail-config.yml
  #   networks:
  #     - backend # (internal only network for traefik.)
  #     - vlanx # (Exposed to Internet)


   # speedtest-exporter:
  #   image: miguelndecarvalho/speedtest-exporter
  #   container_name: speedtest-exporter
  #   environment:
  #     - SPEEDTEST_PORT=9798 #optional
  #     - SPEEDTEST_SERVER=19647 #optional
  #   ports:
  #     - 9798:9798

  NOTES
  #  NOTES ///// NOTES ///// NOTES ///// NOTES ///// NOTES ///// NOTES ///// NOTES ///// NOTES ///// NOTES /////
  # export DOMAIN=traefik.sys.example.com
  #
  #             depends_on:
  #             - cadvisor:cadvisor
  #       - alertmanager:alertmanager

  # volumes:
  #     prometheus_data: {}
  #     grafana_data: {}

  #    node-exporter:
  # image: prom/node-exporter
  # volumes:
  #   - /proc:/host/proc:ro
  #   - /sys:/host/sys:ro
  #   - /:/rootfs:ro
  # command:
  #   - '--path.procfs=/host/proc'
  #   - '--path.sysfs=/host/sys'
  #   - --collector.filesystem.ignored-mount-points
  #   - "^/(sys|proc|dev|host|etc|rootfs/var/lib/docker/containers|rootfs/var/lib/docker/overlay2|rootfs/run/docker/netns|rootfs/var/lib/docker/aufs)($$|/)"
  # ports:
  #   - 9100:9100
  # networks:
  #   - back-tier
  # restart: always
  # deploy:
  #   mode: global

      # - traefik.http.routers.influxdb-http.rule=Host(`influxdb.example.com`)
      # - traefik.http.routers.influxdb-http.entrypoints=http
      # - traefik.http.routers.influxdb-http.middlewares=https-redirect
      # - traefik.http.routers.influxdb-https.rule=Host(`influxdb.example.com`)
      # - traefik.http.routers.influxdb-https.entrypoints=https
      # - traefik.http.routers.influxdb-https.tls=true
      # - traefik.http.services.influxdb.loadbalancer.server.port=8086
      # - traefik.http.services.influxdb.loadbalancer.server.scheme=httproot@zeus:/opt/#docker-data/portainer/compose#