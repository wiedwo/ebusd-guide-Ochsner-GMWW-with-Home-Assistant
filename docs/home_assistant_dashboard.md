# Create Home Assistant dashboard

## Add new card to an existing dashboard
for example: use entities card and add HA sensors ...

or use this yaml-code in **code editor** inside entities card:
```
type: entities
entities:
  - entity: sensor.ebusd_heating_warmwassertemp_soll_05_051_temperature
    name: Warmwassertemp. SOLL 05-051
    secondary_info: last-changed
  - entity: sensor.ebusd_heating_warmwassertemp_aktuell_00_004_temperature
    name: Warmwassertemp. aktuell 00-004
    secondary_info: last-changed
  - entity: sensor.ebusd_heating_warmwasserbereitung_mit_warmepumpe_01_066_status
    name: Warmwasserbereitung mit Wärmepumpe 01-066
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_status_warmwasser_02_052_status
    name: Status Warmwasser 02-052
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_status_waermepumpe_02_053_status
    name: Status Waermepumpe 02-053
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_waermepumpe_betriebsstunden_02_081_hours
    name: Waermepumpe Betriebsstunden 02-081
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_waermepumpe_schaltzyklen_02_080_cycles
    name: Waermepumpe Schaltzyklen 02-080
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_status_heizkreis_02_051_status
    name: Status Heizkreis 02-051
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_status_heizkreispumpe_01_020_status
    name: Status Heizkreispumpe 01-020
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_betriebswahl_heizkreis_03_050_status
    secondary_info: last-updated
    name: Betriebswahl Heizkreis 03-050
  - entity: sensor.ebusd_heating_aktuelle_aussentemperatur_00_000_temperature
    name: Aktuelle Aussentemperatur 00-000
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_vorlauftemp_puffersp_tpo_00_015_temperature
    name: 'Vorlauftemp. Puffersp. TPO 00-015 '
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_vorlauftemp_puffersp_tpm_00_017_temperature
    name: Vorlauftemp. Puffersp. TPM 00-017
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_eintrittstemp_waermequelle_tqe_00_071_temperature
    name: Eintrittstemp. Waermequelle TQE 00-071
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_austrittstemp_waermequelle_tqa_00_070_temperature
    name: 'Austrittstemp. Waermequelle TQA 00-070 '
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_vorlauftemp_waermepumpe_twv_00_007_temperature
    name: Vorlauftemp. Waermepumpe TWV 00-007
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_rucklauftemp_waermepumpe_twr_00_008_temperature
    name: Rücklauftemp. Waermepumpe TWR 00-008
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_sollwert_heizkreis_vorlauftemp_01_002_temperature
    name: Sollwert Heizkreis Vorlauftemp. 01-002
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_istwert_heizkreis_vorlauftemp_00_002_temperature
    name: Istwert Heizkreis Vorlauftemp. 00-002
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_aktueller_raumsollwert_01_001_temperature
    name: Aktueller Raumsollwert 01-001
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_fusspunkt_vorlauftemp_heizen_03_001_temperature
    name: Fusspunkt Vorlauftemp. Heizen 03-001
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_norm_aussentemperatur_03_012_temperature
    name: Norm-Aussentemperatur 03-012
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_vorlauftemp_norm_aussentemp_03_013_temperature
    name: Vorlauftemp. Norm-Aussentemp. 03-013
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_warmwassertemp_spar_05_086_temperature
    name: Warmwassertemp. Spar 05-086
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_heizenergie_mwh_23_010_mwh
    secondary_info: last-updated
    name: Heizenergie MWh 23-010
  - entity: sensor.ebusd_heating_heizenergie_kwh_23_001_kwh
    name: ' Heizenergie kWh 23-001'
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_warmwasserenergie_mwh_23_013_mwh
    name: Warmwasserenergie MWh 23-013
    secondary_info: last-updated
  - entity: sensor.ebusd_heating_warmwasserenergie_kwh_23_066_kwh
    secondary_info: last-updated
    name: Warmwasserenergie kWh 23-066
  - entity: sensor.ebusd_heating_volumenstrom_waermenutzung_21_002_lmin
    secondary_info: last-updated
    name: Volumenstrom Waermenutzung 21-002
  - entity: sensor.ebusd_heating_volumenstrom_waermequelle_21_090_lmin
    secondary_info: last-updated
    name: Volumenstrom Waermequelle 21-090
title: Ochsner WP GMWW 11 plus
```

**finish with next step** 
#
**[Usefull ebusctl commands](ebusctl_commands.md)**


