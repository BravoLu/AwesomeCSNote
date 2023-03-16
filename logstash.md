# Logstash

## Installation

the step of installation refers to the Reference #1

## Start

1. Configure your config file, e.g. /etc/logstash/conf.d/logstash.conf	
   * use [grokdebugger](https://grokdebugger.com/) to debug the grok expression.

```lua
input {
  file {
    path => "/var/log/messages"
    type => "syslog"
    codec => multiline {
      # If the log has multiline, use the below synax to combine them.
      pattern => "^\[%{TIMESTAMP_ISO8601}\]"
      negate => true
      what => "previous"
    }
  }

  file {
    path => "/var/log/secure"
    type => "secure"
  }
}

filter {
  if [type] == "syslog" {
    grok {
      match => { "message" => "%{SYSLOGTIMESTAMP:syslog_timestamp} %{SYSLOGHOST:syslog_hostname} %{DATA:syslog_program}(?:\[%{POSINT:syslog_pid}\])?: %{GREEDYDATA:syslog_message}" }
    }

    syslog_pri { }

    date {
      match => [ "syslog_timestamp", "MMM  d HH:mm:ss", "MMM dd HH:mm:ss" ]
    }
  }
}
        
output {
   elasticsearch {
     hosts => ["your_ip"]
     user => "your_user_name"
     password => "your_password"
     index => "the index of es"
   }          
}

```

2. The key file location

```
# systemd 
/usr/lib/systemd/system/logstash.service
# bin 
/usr/share/logstash/bin/logstash
# config, all the config files in this directory will be loaded.
/etc/logstash/conf.d/ 
```





## Reference 

* https://www.elastic.co/guide/en/logstash/8.6/installing-logstash.html#_yum
* 