# Golang

## Installation

```shell
$ wget https://go.dev/dl/go1.20.5.linux-amd64.tar.gz
$ tar -xvzf go1.20.5.linux-amd64.tar.gz
$ sudo mv go /usr/local/
$ echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
$ source ~/.bashrc
# optional 
$ go env -w GOPROXY=https://goproxy.cn,direct  # setting proxy.
```

