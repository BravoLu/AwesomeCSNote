# Tmux 

## Install pretty tmux 

* Install the dependency 
```shell
# libevent 2.1.8
$ wget https://github.com/libevent/libevent/releases/download/release-2.1.8-stable/libevent-2.1.8-stable.tar.gz
$ tar xzvf libevent-2.1.8-stable.tar.gz
$ cd libevent-2.1.8-stable
$ ./configure & make -j8
$ sudo make install

# ncurses
$ yum install ncurses -y

# check libevent-2.1.so.6
$ ldd tmux 
$ sudo cp /usr/local/lib/libevent-2.1.so.6 /lib64/libevent-2.1.so.6

# install tmux 
$ git clone https://github.com/tmux/tmux.git
$ cd tmux
$ sh autogen.sh
$ ./configure && make -j8
$ sudo make install

# check version of tmux 
$ tmux -V 

# (optional) install pretty tmux, more information refers to https://github.com/gpakosz/.tmux
$ git clone https://github.com/gpakosz/.tmux.git
$ ln -s -f .tmux/.tmux.conf
$ cp .tmux/.tmux.conf.local .
```

## Basic Usage 

### Prefix 

* tmux, default prefix is Ctrl+b


### Session Management 
* Create a new session 
```shell
tmux new -s <session-name>
```

* Split the session
```shell
tmux detach # or ctrl+b d 
```

* List all the sessions 
```shell
tmux ls 
```

* Attach the session
```shell
tmux attach -t 0 # <session-name> 
```

* Kill the session 
```shell
tmux kill-session -t 0 # <session-name>
```

* Rename the session
```
tmux rename-session -t 0 <new-name> 
```