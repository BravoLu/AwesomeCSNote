# filebeat 

## Installation

* Refer to Reference #1 to use `yum` to install filebeat.

## Customize the configure file

1. filebeat configure file location `/etc/filebeat/filebeat.yml`
2. Configure the input section to specify the log files you want to collect:

```yaml
filebeat.inputs:
- type: log
  enabled: true
  paths:
    - /path/to/your/logfile.log
  fields_under_root: true
  fields:
    log_type: your_log_type
```

Replace `/path/to/your/logfile.log` with the actual pathto the log file you want to monitor. If you want to monitor multiple log files, add them as separate entries under `paths`. Replace `your_log_type` with a label to identify the log type (e.g., "application", "webserver", etc.).

3. Configure the Kafka output section.

```yaml
output.kafka:
  enabled: true
  hosts: ["kafka_host:9092"]
  topic: '%{log_type}'
  partition.round_robin:
  	reachable_only: false
  required_acks: 1
  compression: gzip
  max_message_bytes: 1000000
```

4. (Optional) Configure Filebeat to output JSON-encoded log events:

```yaml
processors:
  - decode_json_fields:
  	fields: ["message"]
  	target: ""
  	overwrite_keys: true
```



## Reference 

1. https://www.elastic.co/guide/en/beats/filebeat/8.6/setup-repositories.html#_yum
