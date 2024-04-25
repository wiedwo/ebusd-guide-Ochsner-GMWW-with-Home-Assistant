# Usefull ebusctl commands
you can run ebusctl when you ssh into your home assistant installation.
ssh root@homeassistant.local -p 22222 
(See Debugging the Home Assistant Operating System | Home Assistant Developer Docs 20)
from there you’ll need to get into the docker container running ebusd (supervisor adding are docker containers)

docker exec -it $(docker ps -f name=ebusd -q) /bin/bash

oder:

docker ps --format "{{.ID}} {{.Names}}" | grep "ebusd"

and take the ebusd container ID, then use that in

docker exec -it bc16fa2e5efb /bin/bash

to run bash in the ebusd container. 
you’ll be able to run ebusctl there.
To exit the container => close the putty-session
Befehle auf den EBUS
ebusctl i 
-> Informationen über die gefundenen Geräte, die auf den eBus senden
[...]
address 08: slave #11, scanned "MF=Vaillant;ID=HMU00;SW=0305;HW=0403", loaded
address 76: slave #9, scanned "MF=Vaillant;ID=VWZ00;SW=0305;HW=0403"
[...]

ebusctl scan result 
-> Liefert das Ergebnis eines Scan auf dem Ebus
08;Vaillant;HMU00;0305;0403
15;Vaillant;70000;0419;4603
76;Vaillant;VWZ00;0305;0403

ebusctl r -f State 
-> Lesen des Status der Wärmepumpe
Bsp Ergebnis 100;384;27;heating_water

ebusctl grab 
-> Das Sammeln der unbekannten Nachrichten starten. Das einen Tag lang laufen lassen...

ebusctl grab result 
-> ...und dann mit "ebusctl grab result" die Liste der gefundenen noch nicht dekodierten Nachrichten ausgeben zu lassen.

ebusctl grab result all
 -> liefert auch bereits entschlüsselte Nachrichten.

ebusctl grab result decode
 -> decodiert die Datentypen
ebusctl commands
ebusctl info
2ad9b828-ebusd:/# ebusctl info
version: ebusd 23.2.p20230716
update check: version 23.3 available
device: 192.168.178.68:9999, enhanced, firmware 1.1[4106].1[4106]
access: *
signal: acquired
symbol rate: 35
max symbol rate: 106
min arbitration micros: 3
max arbitration micros: 80
min symbol latency: 8
max symbol latency: 48
scan: finished
reconnects: 0
masters: 4
messages: 70
conditional: 0
poll: 15
update: 7
address 01: master #6
address 03: master #11
address 06: slave #6, scanned "MF=TEM;ID=25440;SW=0113;HW=0000"
address 08: slave #11, scanned "MF=TEM;ID=WE_1 ;SW=3632;HW=3030"
address 10: master #2
address 15: slave #2, scanned "MF=TEM;ID=24849;SW=0605;HW=0102"
address 31: master #8, ebusd
address 36: slave #8, ebusd

ebusctl find
2ad9b828-ebusd:/# ebusctl find
25440 Srerrdata.2nd = no data stored
25440 Srerrdata.3nd = no data stored
25440 Srerrdata.4nd = no data stored
25440 Srerrdata.5nd = no data stored
25440 Srerrdata.6nd = no data stored
25440 Srerrdata.last = no data stored
25440 SRerrdata1.2nd = no data stored
25440 SRerrdata1.3nd = no data stored
25440 SRerrdata1.4nd = no data stored
25440 SRerrdata1.5nd = no data stored
25440 SRerrdata1.6nd = no data stored
25440 SRerrdata1.last = no data stored
25440 SRerrdata2.2nd = no data stored
25440 SRerrdata2.3nd = no data stored
25440 SRerrdata2.4nd = no data stored
25440 SRerrdata2.5nd = no data stored
25440 SRerrdata2.6nd = no data stored
25440 SRerrdata2.last = no data stored
25440 SRerrdata3.2nd = no data stored
25440 SRerrdata3.3nd = no data stored
25440 SRerrdata3.4nd = no data stored
25440 SRerrdata3.5nd = no data stored
25440 SRerrdata3.6nd = no data stored
25440 SRerrdata3.last = no data stored
25440 SRerrdata4.2nd = no data stored
25440 SRerrdata4.3nd = no data stored
25440 SRerrdata4.4nd = no data stored
25440 SRerrdata4.5nd = no data stored
25440 SRerrdata4.6nd = no data stored
25440 SRerrdata4.last = no data stored
25440 unknown.01940048 = no data stored
25440 unknown.01960042 = 150;0;00;8;10.0;0.0;0
25440 unknown.01cc0042 = 204;0;00;8;10.0;0.0;0
25440 unknown.02c60040 = 70;65;04;40;-0.1;0.0;24
25440 unknown.02c80040 = 72;65;04;42;143.9;0.0;236
broadcast datetime = 8.699;21:00:18;15.02.2024
broadcast error = SE60  E OK
broadcast id = no data stored
broadcast id = no data stored
broadcast signoflife = no data stored
heating Aktuelle Aussentemperatur 00-000 = 0;0;0d;°C;50.0;-50.0;8.7
heating Aktueller Raumsollwert 01-001 = no data stored
heating Aussentemperatur Mittelwert 02-020 = 20;1;0d;°C;50.0;-50.0;10.3
heating Austrittstemp. Waermequelle TQA 00-070 = 70;0;0d;°C;100.0;0.0;10.9
heating Betriebswahl Heizung 03-050 = no data stored
heating Eintrittstemp. Waermequelle TQE 00-071 = 71;0;0d;°C;100.0;0.0;15.5
heating Fusspunkt Vorlauftemp. Heizen = 129;65;4d;°C;40.0;10.0;23.0
heating Istwert Heizkreis Vorlauftemp. 00-002 = 130;0;0d;°C;100.0;0.0;32.3
heating Norm-Aussentemperatur 03-012 = 140;65;01;°C;0.5;22.6;-16
heating Rücklauftemp. Waermepumpe TWR 00-008 = 8;0;0d;°C;100.0;0.0;18.1
heating Sollwert Heizkreis Vorlauftemp. 01-002 = 224;0;0d;°C;100.0;0.0;30.3
heating Status Heizkreis 02-051 = 51;1;00;0;25.5;0.0;Heizbetrieb
heating Status Waermepumpe 02-053 = 53;1;00;0;25.5;0.0;Abgeschaltet
heating Status Warmwasser 02-052 = 52;1;00;0;25.5;0.0;Abgeschaltet
heating Vorlauftemp. Norm-Aussentemp. 03-013 = 141;65;00;°C;18.0;31.6;43.0
heating Vorlauftemp. Puffersp. TPM 00-017 = 17;0;0d;°C;100.0;0.0;29.3
heating Vorlauftemp. Puffersp. TPO 00-015 = 15;0;0d;°C;100.0;0.0;32.3
heating Vorlauftemp. Waermepumpe TWV 00-007 = 7;0;0d;°C;100.0;0.0;29.7
heating Waermepumpe Betriebsstunden 02-081 = no data stored
heating Waermepumpe Schaltzyklen 02-080 = no data stored
heating Warmwassertemp. aktuell 00-004 = 4;0;0d;°C;100.0;0.0;37.9
heating Warmwassertemp. Spar 05-086 = 132;0;0d;°C;100.0;0.0;20.0
master 10u0503 = 1;0;0;0.0;0;1
master data1 = 32.301;-;0;0;0;0;0;0;0;29.301
master data2 = 0.000;20.000;0;0;0
scan.06  = TEM;25440;0113;0000
scan.08  = TEM;WE_1 ;3632;3030
scan.15  = TEM;24849;0605;0102


ebusctl grab

ebusctl grab result all decode > /config/ebusd-configuration/grabd.txt

ebusctl decode [-v|-V] [-n|-N] DEFINITION DD[DD]*
  -v          increase verbosity (include names/units/comments)
  -V          be very verbose (include names, units, and comments)
  -n          use numeric value of value=name pairs
  -N          use numeric and named value of value=name pairs
  DEFINITION  field definition (type,divisor/values,unit,comment,...)
  DD          data byte(s) to decode

2ad9b828-ebusd:/# ebusctl decode HCD:3 2c3601
15444
ebusctl decode UCH 000100
***
type	circuit	name	comment	QQ	ZZ	PBSB	ID	field1	part	type	divider/values	unit	comment	field2	part	type	divider/values	unit	comment
r	mixer	temp_mode			50	B504	01	temp		UCH		°C	desired temp.	mode		UCH	1=on;2=off;3=auto;4=eco;5=low		operating mode

QQ    ZZ    PB    SB     ID
10 03 05 0a 00 = 68
10 03 05 02 01 01 = 68
10 fe 05 0d 0a 2c00800000800080ffff = 68
10 fe 10 15  0b 0104020102000000800080 = 6
10 03 05 01 0a ee2414fe00a101000000 = 113
10 03 05 01 0a 554b32fe006401000001 = 9
10 03 05 01 0a 000014fe000000000000 = 150
01 15 06 21 04 068e0040 / 0a0e430000020001000100 = 6


A PS1 file is a script, or "cmdlet," used by Windows PowerShell, 

copy grabd.txt to yourdir
copy scan_ebus_ids.ps1 grabd.txt to yourdir

PC Einstellungen => System => Für Entwickler => Powershell =A Ausführung lokaler powershell scripts erlauben => EIN

cd D:\HomeAssistant\ebus\ebusd\lori
.\scan_ebus_ids.ps1 grabd.txt 
See output on powershell console and test




.\scan_ebus_ids.ps1 grabd.txt








ebusctl r -f

ebusctl r -f  'Aktuelle Aussentemperatur 00-000'
ebusctl r -f  'Istwert Heizkreis Vorlauftemp. 00-002'
ebusctl r -f  'Vorlauftemp. Waermepumpe TWV 00-007'
ebusctl r -f  'Rücklauftemp. Waermepumpe TWR 00-008'
ebusctl r -f  'Vorlauftemp. Puffersp. TPO 00-015'
ebusctl r -f  'Vorlauftemp. Puffersp. TPM 00-017'
ebusctl r -f  'Austrittstemp. Waermequelle TQA 00-070'
ebusctl r -f  'Eintrittstemp. Waermequelle TQE 00-071'
ebusctl r -f  'Vorlauftemp. Anlage 00-096'

ebusctl r -f  'Aktueller Raumsollwert 01-001'
ebusctl r -f  'Sollwert Heizkreis Vorlauftemp. 01-002'
ebusctl r - f 'Warmwassertemp. SOLL aktuell 01-004'
ebusctl r -f  'Status Heizkreispumpe 01-020'
ebusctl r -f  'Status Waermeerzeugerpumpe 01-022'
ebusctl r -f  'Warmwasserbereitung mit Wärmepumpe 01-066'
ebusctl r -f  'Drehzahl Waermeerzeugerpumpe 01-076'

ebusctl r -f  'Aussentemperatur Mittelwert 02-020'
ebusctl r -f  'Status Heizkreis 02-051'
ebusctl r -f  'Status Warmwasser 02-052'
ebusctl r -f  'Warmwassertemp. Spar 05-086'
ebusctl r -f  'Status Waermepumpe 02-053'
ebusctl r -f  'Waermepumpe Schaltzyklen 02-080'
ebusctl r -f  'Waermepumpe Betriebsstunden 02-081'

ebusctl r -f  'Fusspunkt Vorlauftemp. Heizen 03-001'
ebusctl r -f  'Norm-Aussentemperatur 03-012'
ebusctl r -f  'Vorlauftemp. Norm-Aussentemp. 03-013'
ebusctl r -f  'Betriebswahl Heizkreis 03-050'
ebusctl r -f  'Solltemperatur Heizbetrieb 03-051'

ebusctl r -f  'Warmwassertemp. SOLL 05-051'
ebusctl r -f  'Warmwassertemp. Spar 05-086'

ebusctl r -f  'Volumenstrom Waermenutzung 21-002'
ebusctl r -f  'Volumenstrom Waermequelle 21-090'

ebusctl r -f  'Heizenergie kWh 23-001'
ebusctl r -f  'Heizenergie MWh 23-010'
ebusctl r -f  'Warmwasserenergie MWh 23-013'
ebusctl r -f  'Warmwasserenergie kWh 23-066'

ebusctl w -c heating ' Warmwassertemp. SOLL 05-051' 55.0

ebusd config (yaml) 16.01.2024
scanconfig: true
loglevel_all: debug
mqtttopic: ebusd
mqttint: /config/ebusd-configuration/mqtt-hassio.cfg
mqttjson: true
mode: ens
network_device: 192.168.178.68:9999
latency: 30
pollinterval: 10
configpath: /config/ebusd-configuration/ochsner/1521576
accesslevel: "*"
http: false

ebusd config (yaml) 17.01.2024
scanconfig: true
loglevel_all: debug
mqtttopic: ebusd
mqttint: /config/ebusd-configuration/mqtt-hassio.cfg
mqttjson: true
mode: ens
network_device: 192.168.178.68:9999
latency: 30
pollinterval: 10
configpath: /config/ebusd-configuration/ochsner/0625440
accesslevel: "*"
http: false



ebusd config
> ebusd --foreground --mqtthost=core-mosquitto --mqttport=1883 --mqttuser=addons --mqttpass=aing0zeephu2koophooc5Ohl3vitotawoo8ieshohx6hoVaeQuoor5wiedaiShav --scanconfig --mqttjson --configpath=/config/ebusd-configuration/ochsner/0625440 --latency=40 --accesslevel=* --pollinterval=5 --mqttint=/config/ebusd-configuration/mqtt-hassio.cfg --mqttvar="filter-name=" --mqtttopic=ebusd --device=ens:192.168.178.68:9999 --log=all:info


mosquitto_pub

mosquitto_pub -m '?3' -t 'ebusd/heating/Heizenergie MWh 23-010'

https://github.com/john30/ebusd/discussions/1177


TYPE,CIRCUIT,NAME,COMMENT,QQ,ZZ,PBSB,ID

Ebusctl r1,heating,Warmwassertemp. SOLL 05-051,,05b3004e,param


2ad9b828-ebusd:/# ebusctl scan result
1 scan(s) still running
06;TEM;25440;0113;0000
08;TEM;WE_1 ;3632;3030
15;TEM;24849;0605;0102

1524849

> ebusd --foreground --mqtthost=core-mosquitto --mqttport=1883 --mqttuser=addons --mqttpass=Noh3ahth2helo5AoX7CheRiaFoo8in7uv1ohyeiphaith6ohquiedaewookie4Ai --scanconfig --mqttjson --mqttretain --configpath=/config/ebusd-configuration/ochsner/1524849 --latency=40 --accesslevel=* --pollinterval=10 --mqttint=/config/ebusd-configuration/mqtt-hassio.cfg --mqttvar="filter-name=" --mqtttopic=ebusd --device=ens:192.168.178.68:9999 --log=all:info | s6-log 1 n6 s40000000 /config/ebusd-logs/


--checkconfig --dumpconfig=csv --dumpconfigto=/config/ebusd-configuration/ochsner/1860.csv

011506210402c80040 / 0a4841042a9f0500007f05

ebusctl decode "wtime" 0a4841042a9f0500006a05

ebusctl decode "tempt" 011006230605d6004e1800

ebusctl decode "tempt" 01150621046582000e

ebusctl decode "tempt" 011506210405bd004e

ebusctl decode "uch" 011506210401c2004e

Neu:
011506210401c2004e
 01-066 Warmwasser Ladung WP
 	0: Warmwasserbereitung mit Wärmepumpe AUS
	1: Warmwasserbereitung mit Wärmepumpe EIN

Check:
01150621046582000e
011006230605d6004e ??

 05-086

