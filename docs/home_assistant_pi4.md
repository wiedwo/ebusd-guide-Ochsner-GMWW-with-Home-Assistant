# Install Home Assistant on RPi4

By following the [getting started](https://www.home-assistant.io/installation/raspberrypi/) you setup HA on your raspberry Pi. 
You should wire it with a ethernet cable directly to router/switch.

## Install and configure eBUSd AddOn in Home Assistant
- Goto Home Assistant Settings => Add-ons => ADD-On Store => search eBUSd => install
- 
## Install and configure other AddOns and Intergrations (only if not yet done)

- **MQTT Broker:** A message broker that supports the MQTT protocol. It allows for efficient and reliable communication between Home Assistant and ebusd AddOn.
    [Home Assistant MQTT](https://www.home-assistant.io/integrations/mqtt)
- **Advanced SSH & Web Terminal** (to enter HA command-line via SSH)
    [Home Assistant Community Add-on](https://github.com/hassio-addons/addon-ssh)
- **Studio Code Server** or **File editor** (to edit configuration files and watch log files aso)
    [Home Assistant Community Add-on](https://github.com/hassio-addons/addon-vscode)


**proceed with next step** 
#
**[eBUSd on Home Assistant on RPi4](home_assistant_ebusd.md)**
  
