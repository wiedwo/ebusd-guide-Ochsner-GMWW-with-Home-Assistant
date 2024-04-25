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
- Follow the 2-wire cable from the control panel to the adapter
- Connect your 2-wire cable in parallel with the adapter connector in question.
- Connect the USB-cable to power on the adapter
- Power on the heat pump.

# Configure eBUS Adapter with network

- Connect your pc to the WIFI access point with SSID "EBUS" (without password), which is started by the firmware after the first flashing
- use your browser at http://192.168.4.1

- 

The easiest way to make the settings is via network, e.g. via the WIFI access point with SSID "EBUS" (without password), which is started by 
the firmware after the first flashing or after pressing+holding the button during boot (as long as the LEDs are fading). 


Alternatively, the easi> interface can also be operated via a serial connection. This can be done, for example. with the firmware page as explained above, or with Putty, minicom or another terminal program to open the serial USB port (parameters don't matter). Then the easi> interface of the adapter appears, which has umpteen commands for configuration and testing. With "help" these are listed together with parameters. For the Ethernet option, it is recommended to use the initial configuration method described above, as the Ethernet interface must first be configured.
At the same time, a still unconfigured firmware starts a WIFI access point with SSID "EBUS" without a password. If you connect to it, the most important settings can http://192.168.4.1 be easily made on the website.

