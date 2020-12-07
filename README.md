# Spring Boot 2 application metrics using Micrometer
Used Micrometer to capture metrics and Prometheus pulls the metrics

## Reference endpoints
- http://localhost:8080/actuator
- http://localhost:8080/actuator/health
- http://localhost:8080/actuator/metrics
- http://localhost:8080/actuator/metrics/hikaricp.connections.active
- http://localhost:8080/actuator/metrics/jvm.memory.max
- http://localhost:8080/actuator/metrics/http.server.requests
- http://localhost:8080/actuator/metrics/http.server.requests?tag=method:GET
- http://localhost:8080/actuator/prometheus

## Prometheus Configuration
Download Promethus using this [link](https://github.com/prometheus/prometheus/releases/download/v2.23.0/prometheus-2.23.0.windows-amd64.zip) and extract it into a directory.
Add below into `prometheus.yml` file `scrape_configs`:
```yaml
  - job_name: 'spring_boot_actuator'
    metrics_path: '/actuator/prometheus'
    static_configs:
      - targets: ['localhost:8080']
```
