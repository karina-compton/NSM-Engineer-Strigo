# Troubleshooting Demo
Break one thing at a time


## Easy

kibana:

```
set +o history
sudo firewall-cmd --add-port=8000/tcp --permanent
sudo firewall-cmd --remove-port=80/tcp --permanent
sudo firewall-cmd --reload
set -o history
```

## Medium

sensor:

```
set +o history
sudo sed -i 's/9092/9029/g' /usr/share/zeek/site/scripts/kafka.zeek
sudo -u zeek zeekctl deploy
set -o history
```

## Hard

pipeline0, pipeline1, pipeline2

```
set +o history
sudo sed -i 's/suricata-raw/suricata-raww/g' /etc/logstash/conf.d/logstash-100-input-kafka-suricata.conf
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



