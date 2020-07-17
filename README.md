# datadog-zabbix-check

## Overview
Custom check of Datadog agent to collect metrics from Zabbix. It access to Zabbix API and collect item history. Then report them to Datadog as custom metrics.

Operability confirmed at Zabbix 5.0.

## Setup

### Installation

Place `checks.d/zabbix_metrics.py` and `conf.d/zabbix_metrics.d/conf.yaml` files to your Agent's configuration dir(e.g. `/etc/datadog-agent/`).

### Configuration

Edit the `zabbix_metrics.d/conf.yaml` file.

```
init_config:

instances:
  - zabbix_user: "user"
    zabbix_password: "XXXXX"
    zabbix_api: "http://localhost/zabbix/api_jsonrpc.php"

    hosts:
      - "Zabbix server"
      - "Zabbix host"

    metrics:
      - "CPU utilization"
      - "Memory utilization"
```

| Setting  | Description |
| ---- | ----- |
| `zabbix_user` | Username to use Zabbix API. |
| `zabbix_password` | Password of `zabbix_user`. |
| `zabbix_api` | URL for the Zabbix API (e.g. `http://localhost/zabbix/api_jsonrpc.php`) |
| `hosts` | List of hostnames for metrics to be collected. |
| `metrics` | List of Items that collected by Zabbix. |
