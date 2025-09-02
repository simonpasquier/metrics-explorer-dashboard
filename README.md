# metrics-explorer-dashboard

Grafana dashboard to explore Prometheus metrics.

## Requirements

* Grafana (version 11 or above)
* [Grafana Infinity Datasource](https://github.com/grafana/grafana-infinity-datasource)

## How to use it?

1. Configure the Infinity datasource to connect with the base Prometheus URL (it supports TLS and authentication options).
2. Import the dashboard into Grafana and select the configured Infinity datasource.

The dashboard leverages the `/api/v1/status/tsdb`, `/api/v1/series`, `/api/v1/labels` and `/api/v1/label/:label/values` [API endpoints](https://prometheus.io/docs/prometheus/latest/querying/api/). While the requests should be less expensive than using PromQL expressions such as `count by(__name__) ({__name__=~".+"})`, use it with care on environments with lots of metrics.

The dashboard should also work with Thanos Query endpoints, albeit the panels relying on the `/api/v1/status/tsdb` API endpoint.
