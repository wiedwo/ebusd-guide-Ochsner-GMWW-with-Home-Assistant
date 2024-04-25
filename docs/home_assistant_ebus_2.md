# Start eBUSd on Home Assistant

## Start and check eBUSd AddOn in Home Assistant
- Goto Home Assistant Settings => Add-ons => eBUSd => start

## Check protocol
- Goto Home Assistant Settings => Add-ons => eBUSd => protocol

**you should see something like this :**

<details>
<summary>you should see something like this :</summary>
s6-rc: info: service s6rc-oneshot-runner: starting
s6-rc: info: service s6rc-oneshot-runner successfully started
s6-rc: info: service fix-attrs: starting
s6-rc: info: service fix-attrs successfully started
s6-rc: info: service legacy-cont-init: starting
s6-rc: info: service legacy-cont-init successfully started
s6-rc: info: service legacy-services: starting
s6-rc: info: service legacy-services successfully started
> ebusd --foreground --mqtthost=core-mosquitto --mqttport=1883 --mqttuser=addons --mqttpass=Noh3ahth2helo5AoX7CheRiaFoo8in7uv1ohyeiphaith6ohquiedaewookie4Ai --scanconfig --mqttjson --configpath=/config/ebusd-configuration/ochsner/1524849 --latency=40 --accesslevel=* --pollinterval=10 --mqttint=/config/ebusd-configuration/mqtt-hassio.cfg --mqttvar="filter-name=" --mqtttopic=ebusd --device=ens:192.168.178.68:9999 --log=all:info
2024-04-25 18:29:21.066 [main notice] ebusd 23.2.p20230716 started with auto scan on device: 192.168.178.68:9999, enhanced
2024-04-25 18:29:21.067 [main info] loading configuration files from /config/ebusd-configuration/ochsner/1524849/
2024-04-25 18:29:21.067 [main info] reading templates /
2024-04-25 18:29:21.070 [main info] read templates in /
2024-04-25 18:29:21.070 [main info] reading file broadcast.csv
2024-04-25 18:29:21.071 [main info] successfully read file broadcast.csv
2024-04-25 18:29:21.071 [main info] reading file 15.24849.csv
2024-04-25 18:29:21.078 [main info] successfully read file 15.24849.csv
2024-04-25 18:29:21.078 [main info] read config files, got 48 messages
2024-04-25 18:29:21.109 [bus notice] device status: resetting
2024-04-25 18:29:21.110 [bus notice] bus started with own address 31/36
2024-04-25 18:29:21.110 [main info] registering data handlers
2024-04-25 18:29:21.110 [mqtt info] mosquitto version 2.0.18 (compiled with 2.0.15)
2024-04-25 18:29:21.119 [main info] registered data handlers
2024-04-25 18:29:21.123 [bus notice] device status: reset, supports info
2024-04-25 18:29:21.133 [bus notice] device status: extra info: firmware 1.1[431e].1[431e], jumpers 0x03
2024-04-25 18:29:21.146 [bus notice] signal acquired
2024-04-25 18:29:21.146 [bus info] poll cmd: 311506210477840008
2024-04-25 18:29:21.196 [bus info] arbitration delay 7 - 7 micros
2024-04-25 18:29:21.204 [bus info] send/receive symbol latency 7 - 7 ms
2024-04-25 18:29:21.222 [bus info] send/receive symbol latency 7 - 9 ms
2024-04-25 18:29:21.247 [bus info] send/receive symbol latency 6 - 9 ms
2024-04-25 18:29:21.288 [bus info] send/receive symbol latency 6 - 20 ms
2024-04-25 18:29:21.363 [bus notice] new master 10, master count 2
2024-04-25 18:29:21.363 [update info] sent MS cmd: 311506210477840008 / 0a02800d02e80300004101
2024-04-25 18:29:21.363 [update notice] sent poll-read heating Istwert Heizkreis Vorlauftemp. 00-002 QQ=31: 2;0;0d;°C;100.0;0.0;32.1
2024-04-25 18:29:21.524 [mqtt notice] connection established
2024-04-25 18:29:21.539 [mqtt info] received set topic for heating Fusspunkt Vorlauftemp. Heizen 03-001
2024-04-25 18:29:21.539 [bus info] send message: 311006230603810048f000
....
</details>


**proceed with next step** 
#
**[MQTT Explorer on Home Assistant](mqtt_explorer.md)**


