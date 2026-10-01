# mostemplate

MOS Hub -templatet (compose). Jokainen template on kansiossa `compose/<nimi>/`
(`compose.yaml`, `template.json`, valinnainen `.env`), kuvakkeet kansiossa `images/` (200x200 PNG).

| Template | Kuvaus |
|---|---|
| FileBot | Valvoo kansiota, purkaa RAR-releaset, nimeää elokuvat ja sarjat (vaatii lisenssin) |
| PortainerAgent | Portainer Agent, portti 9001 |
| TechnitiumDNS | Technitium DNS Server, hallinta 5380, DNS-osoite `.env`:n `DNS_IP` |
| HomeAssistant | Home Assistant, host-verkko, 8123 |
| ESPHome | ESPHome-dashboard, host-verkko, 6052 |
| EclipseMosquittoMQTT | Mosquitto MQTT 1883 + websocketit 9002, luo oletusasetukset |
| YTZero | YT Zero, YouTube-tilaukset ilman suosituksia, 3001 |
| OpenCloud | Oma pilvitallennus, HTTPS 9200; `.env`:ssä `OC_URL` ja `ADMIN_SALASANA` |
| NodeRED | Node-RED flow-editori, 1880 (ei kirjautumista oletuksena) |

`template.json`: `category` pitää olla taulukko (`["Media"]`), muuten MOS ohittaa sen.
MOS näyttää kuvakkeen vain Hubista asennetuille stackeille.

Kontit, jotka ajetaan käyttäjänä 1000 (OpenCloud, Node-RED), saavat `*-init`-apukontin, joka
antaa root-omisteisiksi luodut bind-kansiot käyttäjälle 1000 ennen käynnistystä.
