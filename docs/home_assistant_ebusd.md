# Configure eBUSd AddOn in Home Assistant
- Goto Home Assistant Settings => Add-ons => eBUSd => configuration
-  use ha_ebusd_config.yaml as a template, but (if possible) avoid to change mqttint: and configpath:
-  do not start eBUSd yet!!
    
## Create an ebusd configuration directory in Home Assistant
- create directory /config/ebusd-configuration
- create directory /config/ebusd-configuration/ochsner
- copy mqtt-hassio.cfg to /config/ebusd-configuration/
- copy _templates.csv to /config/ebusd-configuration/ochsner/1524849
- copy broadcast.csv to /config/ebusd-configuration/ochsner/1524849
- copy gmww11plus.csv to /config/ebusd-configuration/ochsner/1524849
- rename gmww11plus.csv to 15.24849.csv
  
## Check mqtt-hassio.cfg 
- check 'network_device:'
- important note : for including writable messages, use change the line or overwrite with '--mqttvar=filter-direction=r|u|^w'.
  filter-direction = r|u|^w
  
**proceed with next step** 
#
**[MQTT on Home Assistant](mqtt.md)**
