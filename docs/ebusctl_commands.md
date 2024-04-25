# Usefull ebusctl commands
you can run ebusctl when you ssh into your home assistant installation.
ssh root@homeassistant.local -p 22222 
(See Debugging the Home Assistant Operating System | Home Assistant Developer Docs 20)
from there you’ll need to get into the docker container running ebusd (supervisor adding are docker containers)

``docker exec -it $(docker ps -f name=ebusd -q) /bin/bash`` to run bash in the ebusd container.

To exit the container => close the putty-session or "exit"

## ebusctl Befehle 

### ebusctl find

### ebusctl i 
-> Informationen über die gefundenen Geräte, die auf den eBus senden

### ebusctl scan result 
-> Liefert das Ergebnis eines Scan auf dem Ebus

### ebusctl r -f State 
-> Lesen des Status der Wärmepumpe

### ebusctl grab 
-> Das Sammeln der unbekannten Nachrichten starten. Das einen Tag lang laufen lassen.

## ebusctl grab result all decode > /config/ebusd-configuration/grabd.txt
-> die mit "ebusctl grab result" gefundenen noch nicht dekodierten Nachrichten in ein txt-file schreiben.

### ebusctl grab result all
 -> liefert auch bereits entschlüsselte Nachrichten.

### ebusctl grab result decode
### ebusctl decode "tempt" 011006230605d6004e1800 
 -> decodiert die Datentypen

## ebusctl r -f (force read from bus with my "names")

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

## ebusctl w (write to bus , use with care !)
example:
ebusctl w -c heating ' Warmwassertemp. SOLL 05-051' 55.0

#### mosquitto_pub

mosquitto_pub -m '?3' -t 'ebusd/heating/Heizenergie MWh 23-010'


