# Install Home Assistant on RPI4

By following the [getting started](https://www.home-assistant.io/installation/raspberrypi/) you setup HA on your raspberry Pi. 
You should wire it with a ethernet cable directly to router/switch.

## Install and configure eBUSd AddOn in Home Assistant
- Goto Home Assistant Settings => Add-ons => ADD-On Store => search eBUSd => install

## create an ebusd configuration directory in Home Assistant
- create directory /config/ebusd-configuration/
- create directory /config/ebusd-configuration/ochsner
- copy mqtt-hassio.cfg to /config/ebusd-configuration/
- copy _templates.csv to /config/ebusd-configuration/ochsner/1524849
- copy broadcast.csv to /config/ebusd-configuration/ochsner/1524849
- copy gmww11plus.csv to /config/ebusd-configuration/ochsner/1524849
- rename gmww11plus.csv to 15.24849.csv
  
## Check mqtt-hassio.cfg 

- check 'network_device:' and 'configpath:'
- start eBUSd AddOn
- check protocol for errors

---------------------------


```sh
scanconfig: true
loglevel_all: info
mqtttopic: ebusd
mqttint: /config/ebusd-configuration/mqtt-hassio.cfg
mqttjson: true
mode: ens
network_device: 192.168.178.68:9999
latency: 40
pollinterval: 10
configpath: /config/ebusd-configuration/ochsner/1524849
accesslevel: "*"
http: false
mqttvar: "\"filter-name=\""
mqttretain: false
```
- after checking 'network_device:' and 'configpath:' start eBUSd AddOn



Here is a [Install Docker on Raspberry Pi](https://www.simplilearn.com/tutorials/docker-tutorial/raspberry-pi-docker) guide you can follow.

## Docker Volumes

Since container are running in an isolated environment similar to a sandbox, it is recommended to map a volume to each container in order to persist data. Best practise is, to create a ``/home/pi/data`` folder where you store you container specific config files.
Following this aproche you end up with the following structure:

- ``/home/pi/data/ebusd``
- ``/home/pi/data/mqtt_data``
- ``/home/pi/data/node_red_data``
- ``/home/pi/data/portainer_data``

