# Troubleshooting Demo
Break one thing at a time


## Easy

kibana:

```
set +o history
#change elasticsearch.hosts: ["http://elastic0:92OO", "http://elastic1:9200", "http://elastic2:9200"] in /etc/kibana/kibana.yml
sudo systemctl restart kibana
set -o history
```

## Medium

sensor:

```
set +o history
#remove @load /scripts/kafka.zeek in usr/share/zeek/site/local.zeek
sudo -u zeek zeekctl deploy
set -o history
```

## Hard

pipeline0, pipeline1, pipeline2

```
set +o history
change all pipelines from pipelineX:9092 to pipelineX:9200 in
/etc/logstash/conf.d/logstash-100-input-kafka-suricata.conf
sudo systemctl restart logstash
set -o history
```

## More troubleshooting Ideas

sensor

```
set +o history
sudo chown -R root: /data/zeek
sudo -u zeek zeekctl deploy
set -o history
```

```
set +o history
sudo sed -i 's/LogDir = \/data\/zeek/LogDir = \/data\/zeeek/g' /etc/zeek/zeekctl.cfg
sudo -u zeek zeekctl deploy
set -o history
```



