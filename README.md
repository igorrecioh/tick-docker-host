# TICK Stack

This TICK Stack is done for monitoring a host using Docker containers of Telegraf, Chronograf, Kapacitor and InfluxDB.


## Usage

1. Clone repo
 ```bash
 git clone https://github.com/igorrecioh/tick-docker-host.git
 cd tick-docker-host
 ```
2. Generate folder infraestructure
```bash
mkdir -p confs/{telegraf,telegraf/telegraf.d}
```

3. Generate configuration files
```bash
docker run --rm telegraf telegraf config > ./confs/telegraf/telegraf.conf
```

4. Set up Telegraf configuration as commented before

You can modify these settings as desired. Here you have an example of the simplest ones:

```log
[[outputs.influxdb]]
  urls = ["http://influxdb:8086"]
  database = "telegraf" 
  retention_policy = ""
  write_consistency = "any"
  timeout = "5s"
  username = "telegraf"
  password = "password"
```

5. Start the containers (-d option can be added for detached mode)
```bash
docker-compose up
```

## URLs

### Chronograf URL
```
http://localhost:8888
```

### InfluxDB URL
```
http://influxdb:8086
```

### Kapacitor URL
```
http://kapacitor:9092
```

### Based on (Kudos for them)
- `https://github.com/ichasco/tick`
- `https://github.com/nicolargo/docker-influxdb-grafana/`
- `https://tsql.tech/a-self-deployable-tick-stack-for-ingesting-data-monitoring-and-alerting-for-any-service-including-sql-server/` 