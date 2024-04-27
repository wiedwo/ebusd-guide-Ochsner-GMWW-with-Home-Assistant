# Install eBUSd on Home Assistant

## Install and configure eBUSd AddOn in Home Assistant
- Goto Home Assistant Settings => Add-ons => ADD-On Store => search eBUSd => install
- Goto Home Assistant Settings => Add-ons => eBUSd => configuration
- 
## Create an ebusd configuration directory in Home Assistant
- create directory /config/ebusd-configuration
- create directory /config/ebusd-configuration/ochsner
- copy mqtt-hassio.cfg to /config/ebusd-configuration/
- copy _templates.csv to /config/ebusd-configuration/ochsner/1524849
- copy broadcast.csv to /config/ebusd-configuration/ochsner/1524849
- copy gmww11plus.csv to /config/ebusd-configuration/ochsner/1524849
- rename gmww11plus.csv to 15.24849.csv
  
## Check mqtt-hassio.cfg 
- check 'network_device:' and 'configpath:'

**proceed with next step** 
#
**[MQTT on Home Assistant](mqtt.md)**
