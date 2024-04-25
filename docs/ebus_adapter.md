# Connection eBUS Adapter with heat pump

You need to wire the adapter with your heatpump via a eBUS two-wire cable.(You can take a usual KNX wire EIB Y-(ST)-Y 2x2x0,8 for that). 
You should also add a USR-ES1 Modul mit W5500 to connect your adapter with you network via ethernet cable.
For detailed instruction refer to [eBUS Adapter Shield v5 Ethernet](https://adapter.ebusd.eu/v5/#ethernet).
Do not forget, you also need a normal USB-cable with Micro-B-plug.

***Attention: the following description of the connection to my heat pump is without any warranty. Any interference with the heat pump may 
void the warranty! Only do this if you are aware of the risk and accept it.***

**How to wire the adapter with the heatpump ?**
- Shut down the heat pump to avoid electric problems
- Open the top cover of the heat pump
- Follow the 2-wire cable from the OCHSNER front control panel to the OTE adapter
- Connect your 2-wire cable in parallel with the OTE adapter connector in question
  (***Maybe 40, but CHECK CAREFULLY!***)
  ![image](pictures/ote_adapter.png)
- Connect the USB-cable to power on the eBUS adapter
- Power on the heat pump.

# Configure eBUS Adapter with network

- Connect your pc to the WIFI access point with SSID "EBUS" (without password), which is started by the firmware after the first flashing
- use your browser at http://192.168.4.1

![image](pictures/easi1.png)

- define your network WiFi/Ethernet settings and reboot with new ip address
  
![image](pictures/easi2.png)

**Some things won't work at this point, but the network connection needs to work**
#
**Don't worry, proceed with next step** 
#
**[ebusd](./ebusd.md)**
