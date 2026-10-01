# mostemplate

MOS Hub -templatet. Yhden kontin sovellukset ovat suoria Docker-templateja `docker/<Nimi>.json`
(asetukset muokattavissa MOS:n asennusikkunassa), monikonttiset compose-stackeja kansiossa
`compose/<nimi>/` (`compose.yaml`, `template.json`, valinnainen `.env`). Kuvakkeet kansiossa `images/` (200x200 PNG).

| Template | Kuvaus |
|---|---|
| FileBot | Valvoo kansiota, purkaa RAR-releaset, nimeää elokuvat ja sarjat (vaatii lisenssin) |
| PortainerAgent | Portainer Agent, portti 9001 |
| TechnitiumDNS | Technitium DNS Server, hallinta 5380, DNS-osoite `.env`:n `DNS_IP` |
| HomeAssistant | Home Assistant, host-verkko, 8123 |
| ESPHome | ESPHome-dashboard, host-verkko, 6052 |
| EclipseMosquittoMQTT | Mosquitto MQTT 1883 + websocketit 9002, luo oletusasetukset |
| YTZero (docker) | YT Zero, YouTube-tilaukset ilman suosituksia, 3001 |
| OpenCloud (docker) | Oma pilvitallennus, HTTPS 9200; asennuksessa `OC_URL` ja `IDM_ADMIN_PASSWORD` |
| NodeRED (docker) | Node-RED flow-editori, 1880 (ei kirjautumista oletuksena) |

`template.json`: `category` pitää olla taulukko (`["Media"]`), muuten MOS ohittaa sen.
MOS näyttää kuvakkeen vain Hubista asennetuille stackeille.

MOS luo appdata-kansiot root-omisteisina, joten imaget jotka oletuksena ajetaan käyttäjänä 1000
(OpenCloud, Node-RED) ajetaan `--user=0:0`:lla — muuten ne eivät pysty kirjoittamaan kansioihinsa.
