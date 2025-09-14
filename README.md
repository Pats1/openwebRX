### OpenwebRX  Installatie & Configuratie door ON3PDY. ###
---
## Benodigdheden ##
<img src="assets/images/rpi_board.jpg" height="200">      <img src="assets/images/pi5.png" height="200">  <img src="assets/images/antenne.png" height="200">

[**Raspberry Pi**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-5-4gb-11579?_gl=1*lkf79s*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)
Dit is een kleine singleboardcomputer met een ARM-processor.

Deze is in verkrijgbaar in verschillende versies.
Alle versies vanaf een V3 kunnen dienen voor dit project.

[**Behuizing & Koeling**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-behuizing-voor-pi-5-zwart-11584?_gl=1*1a7n6vn*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)

[**Voeding**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-27w-usb-c-power-supply-zwart-eu-11582?_gl=1*p4xdg9*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)
Voeding 5.1V - aansluiting en vermogen hangen af van de gebruikte Raspberry Pi versie.

[**SD kaart**](https://www.kiwi-electronics.com/nl/transcend-32gb-microsd-premium-class-10-uhs-i-plus-adapter-303?search=sd%20kaart)
MicroSD kaart minimaal 8Gb.

**S.D.R's**

SDR-dongles zijn oorspronkelijk ontworpen voor DVB-T HDTV-ontvangst, maar ze zijn prima bruikbaar als SDR.

[**RTL-SDR V3**](https://www.vandijkenelektronica.nl/product/rtl-sdr-v3-tcxo-dongle-500khz-1700mhz-sma-aansluiting/) (is wat ik in gebruik heb)

[**RTL-SDR V4**](https://www.vandijkenelektronica.nl/product/rtl-sdr-v4-tcxo-dongle-500khz-1700mhz-sma-aansluiting/) (geen ervaring mee!)

Persoonlijk heb ik deze modellen in mijn shack. 
- RTL-SDR
- SdrPlay

<img src="assets/images/rtl-sdr.jpg" height="300"><img src="assets/images/sdrplay.jpg" height="300">

**Programma's**
- [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
- [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
- [Win32 Disk Imager](https://win32diskimager.org/)
- [balenaEtcher](https://balenaetcher.en.download.it/download)

---

## Installatie ##

Download de laatste versie via volgende link: [OpenwebRx luarvique](https://github.com/luarvique/openwebrx/releases/)

Kies hier voor het zip bestand (voor een V3 enkel 32bit!, voor V4 kan je zowel de 32 of de 64bit versie gebruiken).

Schrijf het bestand naar de **SD kaart** met behulp van het programma **Raspberry Pi Imager**

<img src="assets/images/rpi_im1.png" width="500">

## Instellen van systeem gebruiker & paswoord! ##

<img src="assets/images/settings_rpim.png" width="500">

Kies hier voor **AANPASSEN** om onderstaand dialoog te openen.

<img src="assets/images/rpi_im2.png" width="500">

- *Hostnaam* ==> vrije keuze voorbeeld: demoSDR
- *Gebruikersnaam* ==> vrije keuze voorbeeld: demoUSR
- *Wachtwoord* ==> vrije keuze demo (opgelet deze is alleen voor het OS)
- *Wiffi instellen* ==> niet nodig voor deze workshop.
- Regio instellingen *Tijdzone:* **Europa/Brussels** en *Toetsenbord indeling:* **be**

Kies **Opslaan** om deze gegevens te bewaren en toe te passen.

<img src="assets/images/rpi_im3.png" width="500">

Klik op **ja** voor deze waarschuwing

mogelijk komt er een bestandsverkener scherm open (negeer waarschuwing en sluit dit)

<img src="assets/images/rpi_im4.png" width="500">
De image wordt nu op de SDkaart geinstalleerd.

<img src="assets/images/rpi_im5.png" width="500">
De installatie wordt geverifieerd

<img src="assets/images/rpi_im6.png" width="500">
Verwijder de SDkaart uit je PC en klik op VERDER GAAN

Om verbinding van op afstand te kunnen maken moet SSH nog worden geactiveerd.

Steek de SDkaart terug in je PC en maak een nieuw leeg tekstbestand aan in de root map met als naam **ssh** (zonder extentie!)

![image](assets/images/ssh.png)

**De eerste opstart van OpenWebRx**

- Steek de SD kaart in de Raspberry PI.
- Sluit de RPI aan in het netwerk.
- sluit de SDR dongle aan op 1 van de USB poorten.
- Sluit de voeding aan en wacht tot deze is opgestart.

Als alles goed is verlopen kan je nu de OpenWebRx openen in je netwerk. **http://demosdr.local:8073/**


## Inloggen op de Raspberry Pi vanop afstand ##
Via een computer in het zelfde netwerk als deze van de Raspeberry Pi kan je inloggen via **SSH** met het programma **PuTTY**.

Hiervoor heb je volgende gegevens voor nodig.
- IP adres van de Raspberry Pi of de hostname **(demosdr.local)**
- gebruikersnaam
- Wachtwoord

De gebruikersnaam en paswoord is wat je hebt opgegegeven in de 'Raspberry Pi Imager'

IP adres: hier moeten we eerst opzoek gaan naar wat er via DHCP is toegekend aan de Raspberry Pi.

Via de opdrachtpromt (CMD) kunnen we dit vinden: ping de hostname die je hebt opgegegeven in 'Raspberry Pi Imager'

```
ping demoSDR
```

![image](assets/images/ping.png)

<img src="assets/images/put_1.png" width="500">

De allereerste keer de PC een verbinding maakt krijg je dit scherm te zien. klik op JA om verder te gaan.

<img src="assets/images/put_2.png" width="500">

Eerst zorgen we dat het OS volledig up to date is. (de allereerste keer kan dit lang duren, geduld ...  +- 8 min)

```
sudo apt-get update
```
```
sudo apt-get upgrade -y
```
```
sudo rpi-update
```
(**eenmalig !!!!!! op eigen risico!!!!!! ** de firmware updaten als je werkt met een oudere V3 RPI) 

De image is zonder de digitale decoders (DMR, NXDN, etc.) via onderstaand commando gaan we deze toevoegen. (kan  lang duren, geduld ...  +- 12 min)

```
sudo install-softmbe.sh
```

>>> *** _start_demoUSR_demo.img *** beschikbaar op USB stick

Nu gaan we een adminin account maken om via de web interface de SDR te kunnen instellen en of aanpassen.

```
sudo openwebrx admin adduser XXXX
```
(XXXX vervangen door een gebruikersnaam en kies een paswoord, als demo gebruik user adminen kies als paswoord ook admin)

<img src="assets/images/put_3.png" width="500">

Nu gaan we herstarten zodat alle updates actief worden.

```
sudo reboot
```

Deze zijn ook interesante commando's betreft gebruiker administratie.

`sudo openwebrx admin adduser` [username]            Add a new user

`sudo openwebrx admin removeuser` [username]         Remove an existing user

`sudo openwebrx admin resetpassword` [username]      Reset a user's password

`sudo openwebrx admin disableuser` [username]        Disable a user

`sudo openwebrx admin enableuser` [username]         Enable a user

`sudo openwebrx admin listusers`                     List enabled users

`sudo openwebrx admin hasuser`                       Test if a user exists

---
### Configureren van de WebSdr ###
---

**Settings ==> General Settings**

Receiver name = ON4TRV

Receiver location = Lubbeek, Belgium

Receiver elevation = 200

Receiver admin = info@trvrienden.be

Receiver band plan = ITU Region 1 (Africa, Europe, Middle East, North Asia)

Receiver coordinates 50,8821422       4,83844307581241

Photo title = Web SDR van de Toffe Radio Amateur Vrienden

Photo description = kopier hier de inhoud van widgets.html (niet verplicht, geeft cluster en solar info in de header)

Receiver Avatar + Receiver Panorama : upload bestanden

Allow users to change center frequency = aanvinken

Magic key = kies een wachtwoord indien je dit wenst. ==> http://localhost:8073/#freq=14000000,mod=usb,sql=-150 **,key=on4trv**

Waterfall color theme = Theme By Teejeez....

**Settings ==> SDR device settings**

<img src="assets/images/dv_1.png" width="800">
Schakel de Airspy HF+ en SDRPlay uit (tenzij je dergelijke SDR hebt)

**Settings ==> SDR device settings ==> RTL-SDR**

<img src="assets/images/ds_1.png" width="800">

indien je meerdere SDR's wil gebruiken moet in bovenstaande nog een Device identifier toevoegen.

om de ***Device serial number*** te vinden kijk je onderaan in het scherm ***Recent device log messages**
<img src="assets/images/ds_2.png" width="800">

Maak de verschillende frequentie banden aan die je wenst te gebruiken.

<img src="assets/images/ps_20m.png" width="800">
<img src="assets/images/ps_17m.png" width="800">
<img src="assets/images/ps_15m.png" width="800">
<img src="assets/images/ps_12m.png" width="800">
<img src="assets/images/ps_11m.png" width="800">
<img src="assets/images/ps_10m.png" width="800">
<img src="assets/images/ps_6m.png" width="800">
<img src="assets/images/ps_4m.png" width="800">
<img src="assets/images/ps_2m.png" width="800">
<img src="assets/images/ps_70cm_1.png" width="800">
<img src="assets/images/ps_70cm_2.png" width="800">
<img src="assets/images/ps_70cm_3.png" width="800">
<img src="assets/images/ps_70cm_4.png" width="800">
<img src="assets/images/ps_70cm_5.png" width="800">
<img src="assets/images/ps_adsb.png" width="800">
<img src="assets/images/ps_pmr.png" width="800">
<img src="assets/images/ps_sat.png" width="800">
<img src="assets/images/ps_ais.png" width="800">

---

***Bookmarks aanpassen of toevoegen***

OpenWebRX+ wordt geleverd met vooraf gedefinieerde bladwijzers voor enkele veelvoorkomende frequenties, zoals weersinformatie, CB-kanalen, enzovoort. Als u deze bladwijzers niet wilt zien, verwijdert u ze en start u OpenWebRX opnieuw op

```
sudo rm -f /etc/openwebrx/bookmarks.d/*
```

```
sudo systemctl restart openwebrx
```

Ik verwijder alleen de CB omdat deze op AM staat.

```
cd /etc/openwebrx/bookmarks.d/
```

```
sudo rm cb.json
```

```
sudo systemctl restart openwebrx
```

*** Eigen Bookmarks plaatsen ***

```
cd /etc/openwebrx/bookmarks.d/
```

```
sudo nano /var/lib/openwebrx/bookmarks.json
```
(deze file bevat de lokale bladwijzers die je zelf toegevoegd)

ga naar bookmarks.json en bovenaan kies je **kopie RAW file**

ga terug naar putty en via een rechts muis klik plak je de configuratie in het leeggemaakte bestand.

CTRL+X ==> save modified buffer Yes


Herstart openWebRX via:

```
sudo systemctl stop openwebrx.service
```

```
sudo systemctl start openwebrx.service
```

---

### installing plugins ###
[openwebrxplus-plugins](https://github.com/0xAF/openwebrxplus-plugins)

Om een ​​plugin(s) te laden moet je een **init.js** bestand aanmaken in je openwebrx installatie.

Om de juiste map te vinden waar bestand moet staan, gebruik je volgend commando.  
```
sudo find / -name openwebrx.js
```

```
cd /usr/lib/python3/dist-packages/htdocs/plugins/receiver
```
vervang **openwebrx.js** door **plugins/receiver**

Tip: wil je zien wat er in deze map staat gebruik **ls -a**

We kopieren het aanwezige voorbeeld naar een nieuw bestand met de juiste naam.  
```
sudo cp init.js.sample init.js
```

Nu gaan we dit bestand editeren met het commando 
```
sudo nano init.js
```

Eerst maken we het bestand compleet leeg zet cursor bovenaan (CTRL+K)

ga naar Plugins.json en bovenaan kies je **kopie RAW file**

ga terug naar putty en via een rechtse muis klik plak je de configuratie in het leeggemaakte bestand.

CTRL+X ==> save modified buffer Yes

```
sudo systemctl restart varnish nginx
```

--- 

Aanbevolen is de RPI een vast IP adres geven. (niet verplicht)

Hiervoor doen we eerst wat opzoeken betrefende het netwerk waarmee we verbonden zijn.

Opniew gebruiken we hiervoor de opdrachtprompt (CMD)  

```
ipconfig
```

Scrol tot je de gegevens van de *Ethernet adapter* ziet. Noteer hier de **Default Gateway**
![image](assets/images/cmd_2.png)

nu zijn we klaar om via **PuTTY** de instelling van de RPI aan te passen. 

```
sudo nmtui
```

Met de pijltjes omhoog/omlaag en de met de tabtoets navigeer je door deze dialogen.

<img src="assets/images/eth_1.png" width="400">

voor het aanpassen van het IP adress gebruik je ***Edit a connection***

<img src="assets/images/eth_2.png" width="400">

Activeer (blauw) ***de Wired connection 1*** , zet je (rood) ***Edit..*** actief en via de Enter toets ga je naar volgende scherm.

<img src="assets/images/eth_3.png" width="400">

Zet IPv4 van Automatic naar Manual

<img src="assets/images/eth_4.png" width="400">

Zet achteraan ***show*** actief en enter.

<img src="assets/images/eth_5.png" width="400">

TIP: gebruik als ***Addresses*** dat wat momenteel via DHCP is toegekend aan de Raspberry Pi. (zo ben je zeker van geen conflicten!).

Opgelet /24 moet achteraan het gewenste IP adres staan!

***Gateway** daar gebruik je de **Default Gateway** die je hebt verkregen via **ipconfig**

***DNS servers*** hier gebruik ik 1.1.1.1(google) of 8.8.8.8(cloudflare) voor.

Via de Tabtoets zet je ***OK** actief en druk je op enter.

Je komt nu terug in het vorige dialoog activeer (Tabtoets) ***Back** en druk op enter.

Je komt nu terug in het vorige dialoog activeer (met de pijltjes) ***Quit** en druk op enter.

```
sudo reboot
```
zal de wijzigingen activeren.

Tip: via dit kan ook indien gewenst de hostnaam worden aangepast.

---

**BACKUP maken !!!**

hiervoor gebruik ik Win32 Disk Imager. 

Navigeer naar een folder en geef een zinvolle bestandsnaam op gevolgd door **.img**

Selecteer het juiste doelapparaat. Klik op Lezen en wacht tot het inlezen voltooid is.

<img src="assets/images/winD32.png" width="500">

Bewaar dit op een veilige plaats Tip: bewaar ook de login gegevens op die plaats in een tekstbestand.

PiShrink
PiShrink is a bash script that automatically shrink a pi image that will then resize to the max size of the SD card on boot. 
This will make putting the image back onto the SD card faster.
PiShrink can be ran on Windows using Windows Subsystem for Linux (WSL 2)

In an Administrator command prompt run wsl --install -d Debian. You will likely need to reboot after. 
Open the Debian or Ubuntu app from your start menu.
Your C:\ drive is mounted at /mnt/c/ of when multi /d/ /e/ etc.

Installation
Run sudo apt update && sudo apt install -y wget parted gzip pigz xz-utils udev e2fsprogs
wget https://raw.githubusercontent.com/Drewsif/PiShrink/master/pishrink.sh
chmod +x pishrink.sh
sudo mv pishrink.sh /usr/local/bin

Usage
cd /mnt/c/
ls -a
sudo /usr/local/bin/pishrink.sh demoUSR_demo.img demoUSR_demo_reduced.img
---

**Herstellen VIA een reeds opgeslagen backup**

Hiervoor gebruik ik bij voorkeur balenaEtcher (niet nodig om een zip of rar bestand uit te pakken)
<img src="assets/images/etcher.png" width="700">

Na het schrijven de SDkaart terug in de RPI plaatsen en opstarten.

Krijg je onderstaande klik op annuleren en sluit het scherm.

<img src="assets/images/error.png" width="300">

---

***User & Paswoord wijzigen***

```
sudo adduser newuser_name
```

```
sudo usermod newuser_name -a -G openwebrx,adm,dialout,cdrom,sudo,audio,video,plugdev,games,users,input,netdev,spi,i2c,gpio
```

---

**SDR op het internet**

Maak een gratis account aan op [Cloudflare](https://dash.cloudflare.com)

```
sudo apt install curl lsb-release
```
```
curl -L https://pkg.cloudflare.com/cloudflare-main.gpg | sudo tee /usr/share/keyrings/cloudflare-archive-keyring.gpg >/dev/null
```
```
echo "deb [signed-by=/usr/share/keyrings/cloudflare-archive-keyring.gpg] https://pkg.cloudflare.com/cloudflared $(lsb_release -cs) main" | sudo tee  /etc/apt/sources.list.d/cloudflared.list
```
```
sudo apt update
```
```
sudo apt install cloudflared
```

---

armhf architecture (32-bit Raspberry Pi)

```
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-arm
sudo mv -f ./cloudflared-linux-arm /usr/local/bin/cloudflared
sudo chmod +x /usr/local/bin/cloudflared
cloudflared -v
```

arm64 architecture (64-bit Raspberry Pi)

```
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-arm64
sudo mv -f ./cloudflared-linux-arm64 /usr/local/bin/cloudflared
sudo chmod +x /usr/local/bin/cloudflared
cloudflared -v
```

kies ***If you already have cloudflared installed on your machine:*** en kopier dit naar het bureaublad.

VB: ` sudo cloudflared service install eyJhIjoiMDEz....9`

---

**Interesante links**

[Cheatsheets/Learn Raspberry Pi](https://www.codecademy.com/learn/learn-raspberry-pi/modules/raspberry-pi-command-line-module/cheatsheet)

[rtl-sdr](https://www.rtl-sdr.com/)

[FREQUENTIE DATABASE](https://frequentiedatabase.eu/zoekfreq.php)

[sigidwiki](https://www.sigidwiki.com/wiki/Signal_Identification_Guide)

---
















