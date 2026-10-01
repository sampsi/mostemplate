# mostemplate

MOS Hub -templatet suorina Docker-templateina: `docker/<Nimi>.json` (yksi kontti, asetukset
muokattavissa MOS:n asennusikkunassa). Kuvakkeet kansiossa `images/` (200x200 PNG).

| Template | Kuvaus |
|---|---|
| FileBot | Valvoo kansiota `odottaa/`, purkaa RAR-releaset, nimeää elokuvat ja sarjat (vaatii lisenssin) |
| PortainerAgent | Portainer Agent, portti 9001 |
| TechnitiumDNS | Technitium DNS Server, hallinta 5380, DNS 53 sidottuna LAN-osoitteeseen (oletus 192.168.1.10) |
| HomeAssistant | Home Assistant, host-verkko, 8123 |
| ESPHome | ESPHome-dashboard, host-verkko, 6052 |
| EclipseMosquittoMQTT | Mosquitto MQTT 1883 + websocketit 9002, luo oletusasetukset |
| YTZero | YT Zero, YouTube-tilaukset ilman suosituksia, 3001 |
| OpenCloud | Oma pilvitallennus, HTTPS 9200; asennuksessa `OC_URL` ja `IDM_ADMIN_PASSWORD` |
| NodeRED | Node-RED flow-editori, 1880 (ei kirjautumista oletuksena) |

Huomioita:

- `category` pitää olla taulukko (`["Media"]`), muuten MOS ohittaa sen.
- MOS rakentaa komennon `mos-deploy_docker`-skriptillä: `extra_parameters` ja `post_parameters`
  pilkotaan `xargs`:lla, joten lainausmerkit toimivat (esim. `--entrypoint=sh` + `-c "..."`).
  `TZ` lisätään automaattisesti.
- MOS luo appdata-kansiot root-omisteisina, joten imaget jotka oletuksena ajetaan käyttäjänä 1000
  (OpenCloud, Node-RED) ajetaan `--user=0:0`:lla — muuten ne eivät pysty kirjoittamaan kansioihinsa.
- Portin `host`-kenttään voi laittaa myös `IP:portti` (Technitiumin DNS).
