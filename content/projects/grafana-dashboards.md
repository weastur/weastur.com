+++
categories = ["devops"]
coders = []
date = 2021-04-15
keywords = ["grafana", "dashboard", "metrics", "visualization", "prometheus"]
description = "Set of useful Grafana dashboards"
github = ["https://github.com/weastur/grafana-dashboards"]
title = "Grafana dashboards"
type = "post"
[[tech]]
logo = "images/prometheus.svg"
name = "Prometheus"
url = "https://prometheus.io/"
[[tech]]
logo = "images/grafana.svg"
name = "Grafana"
url = "https://grafana.com/"
+++

Set of useful Grafana dashboards

## List

1. [ClickHouse](https://github.com/weastur/grafana-dashboards/tree/d7b80d79f2c8582413bb30fa8055a0f547e79a3d/dashboards/clickhouse)

## Development

### Requirements

1. Docker
1. docker-compose

### Flow

1. Up environment
    ```bash
    docker-compose up -d
    ```
1. Go to Grafana: http://127.0.0.1:3000 (admin/admin)
1. Connect Prometheus: http://127.0.0.1:9090
1. Import dashboards.
1. Make your changes
1. Export your dashboard and save it to appropriate folder

## License

MIT, see [LICENSE](https://github.com/weastur/grafana-dashboards/blob/d7b80d79f2c8582413bb30fa8055a0f547e79a3d/LICENSE).
