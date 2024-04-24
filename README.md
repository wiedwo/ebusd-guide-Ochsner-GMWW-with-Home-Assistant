# ebusd-ochsner

This repository describes how to setup a infrastructure to control a eBUS based heating pump, **in this case:**
 - **Ochsner GMWW 11 plus (OTE3)** (smaller and bigger models may also work)
 - **Home Assistant** (Open source home automation that runs on a Raspberry Pi or a local server)

You can setup the same for every other eBUS based heating pump, the only difference are the ebusd specific configurations.

## Helpful links

The following links are very helpful and might help understanding different topcis

- [Home Assistant Installation](https://www.home-assistant.io/installation/)
- [ebusd wiki](https://github.com/john30/ebusd/wiki)
- [eBUS Adapter Shield v5](https://adapter.ebusd.eu/v5/)
- [A xxxxxx Node-RED](https://noderedguide.com/nr-lecture-1/)
- [MQTT beginner’s guide](https://www.u-blox.com/en/blogs/insights/mqtt-beginners-guide#:~:text=MQTT%20is%20a%20publish%2Dand,topics%20handled%20by%20a%20broker.)
- [Why XXXXX](https://www.xxxxxiner.io/why-portainer)

## Component overview

```mermaid
%%{init: {'theme':'dark'}}%%
graph LR  
    subgraph Heating System  
        Pump[Heating Pump] -->|controls| Adapter[eBus Adapter]  
        Pi[Raspberry Pi] -->|uses| Adapter  
        Router[Router] -->|network connection| Pi  
        Router -->|network connection| Adapter  
  
        subgraph Raspberry Pi  
            subgraph Home Assistant  
                NodeRed[Node-RED]  
                Ebusd[ebusd]  
                MqttBroker[MQTT Broker]  
                Portainer[internal Portainer]
                Docker -->|communicates with| Adapter 
            end  
  
            NodeRed -->|publishes/subscribes| MqttBroker  
            Ebusd -->|publishes/subscribes| MqttBroker  
            Portainer -->|manages| Docker  
        end  
    end  

```

The heating system is composed of several interconnected components that work together to control and monitor the heating pump. The central control unit of this system is a Raspberry Pi, which is connected to the network via a general router.

### Components

- **Heating Pump:** The primary device responsible for circulating heat transfer fluid throughout the heating system.
- **eBus Adapter:** An interface device that enables communication between the heating pump and the Raspberry Pi.
- **Router:** A network device that facilitates data communication between the Raspberry Pi, the eBus Adapter, and potentially other networked devices.
- **Raspberry Pi:** A compact computer that hosts a Home Assistant environment and serves as the brain of the system. It uses the eBus Adapter to interface with the heating pump.

### Home Assistant (HA) on Raspberry Pi

**It is highly recommended to have sufficient knowledge how to install and operate Home Assistant prior to install and operate ebusd !!** (This is not part of manual)
###It is highly recommended to have sufficient knowledge how to install and operate Home Assistant prior to install and operate ebusd !! (This is not part of manual)
Within the Raspberry Pi, the Home Assistant host is running to manage and isolate different software components using (internal!) containers. The software components are called
Add-On's or integrations.
The following Add-On's are in operation:

- **ebusd:** A daemon for handling communication with eBus devices like the heating pump. It interfaces with the eBus Adapter to control and monitor the pump.
- **MQTT Broker:** A message broker that supports the MQTT protocol. It allows for efficient and reliable communication between Home Assistant and ebusd AddOn.
- **Advanced SSH & Web Terminal** (to enter HA command-line via SSH)
- **Studio Code Server** or **File editor** (to edit configuration files and watch log files aso)
- Node-RED: Can be used, but not needed here (programming tool to create automation flows).
- Portainer: Can be used, but not needed here (management tool to manage the internal Docker containers).

### Network Connections

The Raspberry Pi and the eBus Adapter both connect to the network through the Router, enabling remote access and control. This setup allows for monitoring and managing the heating system from a networked computer or a smart device.
>You can also connect the eBUS adapter via usb to your raspberry Pi, there it might be necessary to install ebusd directly on you raspberry Pi instead of running them inside a docker container.

The Docker containers on the Raspberry Pi communicate with each other and with external devices through the MQTT Broker and eBus Adapter, creating a robust and flexible control system for the heating pump.

## Step by step guide

The following steps provide a step by step guide to setup such an environment from the scratch.

1) [Raspberry Pi and Docker](./docs/raspberry_pi_docker.md)
2) [eBUS Adapter Shield v5](./docs/ebus_adapter.md)
3) [Portainer](./docs/portainer.md)
4) [MQTT](./docs/mqtt.md)
5) [ebusd](./docs/ebusd.md)
6) [Node-RED](./docs/nodered.md)
