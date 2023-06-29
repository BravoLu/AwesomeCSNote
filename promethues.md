# Promethues 

## Installation

```shell
$ wget https://github.com/prometheus/prometheus/releases/download/v2.45.0/prometheus-2.45.0.linux-amd64.tar.gz
$ tar -xvzf prometheus-2.45.0.linux-amd64.tar.gz
```

## Setup

* add user and group of prometheus.

```shell
$ sudo useradd -m -s /bin/bash prometheus
$ sudo groupadd prometheus
$ sudo usermod -aG prometheus prometheus
$ sudo chown -R prometheus:prometheus /path/to/prometheus
```

* use systemd to start prometheus.

```shell
$ sudo vim /etc/systemd/system/prometheus.service
```

* edit /etc/systemd/system/prometheus.service

```yaml
[Unit]
Description=Prometheus Server
Documentation=https://prometheus.io/docs/introduction/overview/
After=network-online.target

[Service]
User=prometheus
Group=prometheus
Type=simple
ExecStart=/path/to/prometheus/prometheus --config.file=/path/to/prometheus/prometheus.yml --storage.tsdb.path=/path/to/prometheus/data

[Install]
WantedBy=multi-user.target
```

* reload systemctl

```shell
$ sudo systemctl daemon-reload
$ sudo systemctl restart prometheus
$ sudo systemctl status prometheus
```

