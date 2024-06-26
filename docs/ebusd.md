# eBUSd Adjustments

## Adapting ebusd configuration

For experienced users:

### national language in 15.24849.csv

In the configuration, you find the eBUS-ID in the name field.

It has the format XX-XXX for instance the ``Warmwassertemp. SOLL 05-051`` with id ``05-051``.
The eBUS-ID can be found in the follwing Ochsner manual: "Bedienungsanleitung Wärmepumpenregler OTE 3/OTE 4".

**In my configuration i used the german names, but it is no problem to change to english names, but it should be done
prior to use the configuration-file ``15.24849.csv`` for the first time.** (remember gmww11plus.csv was renamed to
15.24849.csv in a prior step)

Note: changing the names in ``15.24849.csv`` will create new (duplicate) sensor-names in Home Assistant !!
#

### Missing values
Due to older/newer HW- and SW-versions it could be possible, that you get no values for some name fields.

To find the correct address in your environment, you need to use the ebusd ``ebusctl grap result all decode`` command.
To use the ebusctl command-line feature you have to connect to Home Assistant via SSH.

To connect to the (internal) ebusd container in Home Assistant you can use two different tools:
#
**1) Home Assistant "Advanced SSH & Web Terminal"**

![image](pictures/advanced_ssh&web_terminal.png)

#
**2) Putty**

![image](pictures/putty_conf.png)

#
### ebusctl commands

1) run ``docker exec -it $(docker ps -f name=ebusd -q) /bin/bash`` 
2) run ``ebusctl grab`` and wait for at least 24 hours
3) Run ``ebusctl grab result all decode > /config/ebusd-configuration/grabd.txt`` to write the decode content into the ``/config/ebusd-configuration/grabd.txt`` file
4) Open a file viewer e.g. notepad++ and search for the desired eBUS-ID
5) Search for the eBUS-ID ``05-051`` and look for the TEM_P XXXX= prefix.

```txt
...
TEM_P b342=05-051, 428d=26-066, 8d02=05-013, 0258=16-002, 5802=04-088, 0264=08-002, 6400=00-100, 00f4=08-000, f401=03-116
...
```

6) Scroll upwards until you find a address block with the structure ``XXXXXXXXXXXXXXXXXX / XXXXXXXXXXXXXXXXXXXXXX``

```txt
...
31150621046580000e / 0ab3428d0258026400f401 = 9
...
```
7) The final address are the last 8 characters of the first segment ``6580000e``
8) Go to your config and change the address of the corresponding row

```csv
r1,,temperature.hotwater.normal.set,05-051 Setpoint desired hot water temperature,,,,6580000e,,,param,,,,,,tempt,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,
w,,temperature.hotwater.normal.set,05-051 Setpoint desired hot water temperature,,,,6580000e,,,tempt,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,
```
9) change the address found in ``/config/ebusd-configuration/ochsner/1524849/15.24849.csv`` file and **override** the existing one
10) In order to reload the configuration, you have to stop/start the ebusd AddOn.

## Script for scanning decoded output

There is a Windows powershell script for printing out the eBUS-Ids and the corresponding addresses, which enables much faster address detection than searching manually.

Therefor follow the steps above until step 4 (download the decoded output file to your local computer) and execute the following [script](https://github.com/Lorilatschki/ebusd-ochsner/blob/main/scan_ebus_ids.ps1) in a Windows PowerShell environment:

```ps1
.\scan_ebus_ids.ps1 PATH_TO_DECODED_TXT_FILE
```
#
**in case of authorization problems, goto:** PC Settings => System => For Developers => Powershell => Allow Local PowerShell Scripts to Run => ON
#
The output (in PowerShell console) looks similar to that:
<details>
  <summary>scan output</summary>

```log
00-000 -> 0000e300,00800040,00800042
00-003 -> 6400f401,ec013000
00-004 -> 00840040
00-007 -> 00870042
00-008 -> 00880042,7d820002
00-015 -> 7a800010
00-017 -> 7a810010
00-070 -> 00c60042
00-071 -> 00c70042
00-096 -> 00e00040
01-001 -> 7784000a
01-004 -> 7982000e
01-022 -> 01960042
01-076 -> 01cc0042
01-096 -> 7a830010
02-000 -> 00009803,0000a703,91103100
02-001 -> 00000100,00002f01
02-020 -> 7782000a
02-051 -> 7780000a
02-052 -> 7980000e
02-053 -> 02b50040,7d800002,7e800004
02-070 -> 02c60040
02-072 -> 02c80040
02-080 -> 7d850002,7e820004
02-081 -> 7d860002,7e830004
03-050 -> 03b2004a
04-000 -> 0000e300
04-001 -> 00000002,0000d200
04-003 -> 00000000,00000100
05-050 -> 05b2004e
05-051 -> 6580000e
05-086 -> 05d6004e
06-002 -> 00000100,0000d200
06-003 -> 00005e01,6400b400
06-005 -> 02012800,0a002300
06-014 -> 068e0040
08-000 -> 00003301,00005e01
08-001 -> 0000ff01,6400d200
08-003 -> 02012800,9cff9600
09-075 -> 61800002
10-003 -> 3c014c00,6400d200,ec013000
10-004 -> 00002a01,0cfe3700,1e000900,45495320
12-002 -> 00000000,00000002,0000ff01
12-003 -> 6400b400,6400d200
12-005 -> 6400f401
14-003 -> 00000100
16-002 -> 00005ab1
16-003 -> 3c014c00,6400d200
21-002 -> 7d870002
21-090 -> 7d880002
23-001 -> 7d890002,7e840004
23-005 -> 7d8b0002
23-006 -> 7d8d0002
23-010 -> 7d8a0002,7e850004
23-012 -> 7d8c0002
23-013 -> 7d8e0002
26-003 -> 6400d200,9cff9600
30-063 -> 00000000,00000002,00001f01,00002701,00002b01,00002c01,00002d01,00002e01,00002f01,00003001,00005ab1,00009703,00009a03,00009c03,00009e03,0000a003,0000a103,0000a303,0000a603,0000a903,0000ab03,0000ad03,0000af03,0000b203,0000b403,0000b503,0000e200,0000e300,0000fe01,0000ff01,0a002300,0cfe3700,0cfe3800,0cfe3a00,0cfe3d00,0cfe3e00,0cfe3f00,0cfe4100,0cfe4200,0cfe430030-127 -> 03040601
```
</details>

>Sometime there are multiple addresses behind a eBUS-ID, therefor you need to take a look at the data in order to find the desired correct eBUS address.

## Testing ebusd signals

In order to test whether your MQTT broker recieves messages from the ebusd, you can use the tool ``MQTT Explorer``. It can be downloaded [here](https://mqtt-explorer.com/).

### Read Signals

Once you have setup the eBUS adapter, the docker containers ebusd and mqtt, you should see incoming messages with topic ``ebusd/*``.

![image](pictures/mqtt_explorer.png)

### Write Signals

To verify if you can change a writable eBUS address, you must append ``/set`` to the topic, switch to raw format, type in the desired value and click publish. To verify if the value has been changed by your headpump, go to the OTE display and double check it.

![image](pictures/mqtt_explorer_set.png)

**proceed with next step** 
#
**[Create Home Assistant dashboard](home_assistant_dashboard.md)**
