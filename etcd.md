# etcd

## installation

```shell
$ wget https://github.com/etcd-io/etcd/releases/download/v3.5.0/etcd-v3.5.0-linux-amd64.tar.gz
$ tar xzvf etcd-v3.5.0-linux-amd64.tar.gz
$ sudo mv etcd-v3.5.0-linux-amd64/etcd* /usr/local/bin/
$ sudo useradd -r -s /usr/sbin/nologin etcd
$ sudo mkdir -p /var/lib/etcd/
$ sudo chown etcd:etcd /var/lib/etcd/
$ sudo chown etcd:etcd /usr/local/bin/etcd
```

## Configuration

```yaml
# sudo vim /etc/systemd/system/etcd.service
[Unit]
Description=etcd
After=network.target

[Service]
User=etcd
Type=notify
ExecStart=/usr/local/bin/etcd \
  --name etcd-node-1 \
  --initial-advertise-peer-urls http://<etcd-node-1-ip>:2380 \
  --listen-peer-urls http://<etcd-node-1-ip>:2380 \
  --listen-client-urls http://<etcd-node-1-ip>:2379,http://127.0.0.1:2379 \
  --advertise-client-urls http://<etcd-node-1-ip>:2379 \
  --initial-cluster-token etcd-cluster-1 \
  --initial-cluster etcd-node-1=http://<etcd-node-1-ip>:2380,etcd-node-2=http://<etcd-node-2-ip>:2380,etcd-node-3=http://<etcd-node-3-ip>:2380 \
  --initial-cluster-state new \
  --data-dir /var/lib/etcd/

[Install]
WantedBy=multi-user.target

# single node
[Unit]
Description=etcd
After=network.target

[Service]
User=$USER
Type=notify
ExecStart=/usr/local/bin/etcd \
  --name etcd-node-1 \
  --listen-client-urls http://0.0.0.0:2379 \
  --advertise-client-urls http://localhost:2379 \
  --data-dir /var/lib/etcd/
```



