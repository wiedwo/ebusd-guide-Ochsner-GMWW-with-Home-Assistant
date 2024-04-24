# Install Home Assistant on RPI4

By following the [getting started](https://www.home-assistant.io/installation/raspberrypi/) you setup HA on your raspberry Pi. 
**You should wire it with a ethernet cable directly to router/switch.**

## Docker on Raspberry Pi

Here is a [Install Docker on Raspberry Pi](https://www.simplilearn.com/tutorials/docker-tutorial/raspberry-pi-docker) guide you can follow.

## Docker Volumes

Since container are running in an isolated environment similar to a sandbox, it is recommended to map a volume to each container in order to persist data. Best practise is, to create a ``/home/pi/data`` folder where you store you container specific config files.
Following this aproche you end up with the following structure:

- ``/home/pi/data/ebusd``
- ``/home/pi/data/mqtt_data``
- ``/home/pi/data/node_red_data``
- ``/home/pi/data/portainer_data``
