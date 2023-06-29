# Grafana
## Installation

```shell
$ sudo apt-get install -y adduser libfontconfig1
$ wget https://dl.grafana.com/enterprise/release/grafana-enterprise_10.0.0_amd64.deb
$ sudo dpkg -i grafana-enterprise_10.0.0_amd64.deb
$ sudo systemctl start grafana-server
```

## Configuration

* /etc/grafana/grafana.ini