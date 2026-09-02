---
publish: true
title: Disseny Segur i Seguretat Perimetral
tags:
  - apunts
  - ic10/0226
  - ic10/0226/RA4
---

# Llicència

Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2025 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---

# Wifi

## Atacs als AP

Com ataquem les diferents mesures de seguretat que es poden implementar en un AP?

Utilitzarem una eina en Python anomenada `wifite2` que podeu trobar [al seu GitHub](https://github.com/derv82/wifite2).

![[IC10/0226/RA4/Pasted image 20260410095257.png]]

### WEB

- Atac de força bruta obtenint un conjunt significatiu de paquets e intentant decodificar la clau. Un cop obtinguts els paquets (procés que es pot accelerar amb un atac paral·lel de repetició) crackejar la clau són pocs minuts. En condicions óptimes aquest atac pot durar entre 5 i 10 minuts.

### WPA / WPA2 / WPA3

#### PSK

- Cracking de la contrasenya, totalment depenent de la seva seguretat.

#### AES

Atac de spoofing (_Evil Twin_).  Aquest no es pot fer amb wifite, però podeu probar [Wifi Pumpkin3](https://github.com/P0cL4bs/wifipumpkin3).

### Filtratge MAC

Mesura de seguretat típica en portals captius.

- `Wireshark` i `Mac Changer`.

### Amagar el SSID

- `Wireshark`.

### WPS

Com ha hem vist, amb un atac `pixie dust`.

## Atacs a clients

### Wifi Jamming

- [dw](https://github.com/ndyakov/dw/): Desautenticador per a determinats clients.
- [netattack](https://github.com/chrizator/netattack/)
- [wifijammer](https://github.com/DanMcInerney/wifijammer/)

### Wifi Beacons: ¿on s'ha estat?

Protocol 802.11 té algunes coses interessants de per si:

- Beacons per a reconnectar a xarxes preferides o guardades.
- Paquet de desconnexió de client sense necessitat d'estar connectat a la xarxa.

`sudo airmon-ng start wlan0`
`sudo wireshark`
I dins de Wireshark, filtar per: `wlan.fc.type_subtype eq 4 && wlan.mgt != ""`

![[IC10/0226/RA4/Pasted image 20260410095711.png]]

Amb la MAC d'origen podem saber la marca del dispositiu en web com <https://www.macvendorlookup.com/>. Tot i que actualment ja no es cert, ja que per mantenir certa privasitat els alguns dispositius Wifi muten la MAC  de forma aleatoria.

Amb el `SSID` podem consultar BBDD de _wardriving_ com <https://wigle.net/> per geolocalitzar la wifi.

## Detecció i defensa

- [Wirless IDS](https://github.com/SYWorks/wireless-ids).

# SDR

Freqüències altament regulades! Preill en emetre i que triangulin la senyal.

## Radio

- Manresa: `95.8 MHz` FM
- Flashback: `99.8 MHz` FM

## Escolta avions / baixells

### Avions

APP Barcelona APP 121.150 H24 APP-H 119.100 H24 APP-L 124.700 H24 BACK-UP 125.250 H24 APP-H 126.500 H24 APP-H 127.700 H24 APP-H 131.125 H24 APP 135.275 H24 APP TWR Barcelona TWR 118.100 H24 LOCAL ARR 118.325 H24 LOCAL DEP 121.650 H24 GMC C 121.700 H24 GMC N 121.800 H24 CLR 122.225 H24 GMC S 121.500 H24 EMERG 243.000 H24 EMERG 257.800 H24 MIL ATIS Barcelona Information 118.650 H24 ARR 121.975 H24 DEP D-ATIS Barcelona Information NIL H24 Suministro de información ATIS mediante enlace de datos / Provision of ATIS information via data link.

FRECUENCIAS AEROPUERTO SABADELL

TWR Sabadell TWR 120.800 HR AD 121.600 HR AD GMC 121.500 HR AD EMERG VDF Sabadell gonio 120.800 HR AD 121.500 HR AD 121.600 HR AD A/G 123.500 HR AD Aeroclub / Flying club

<https://aterriza.org/pistas-en-google-map/> Manresa-Bages LEMS: `119.200` Sallent-Pla de Bages (Esc): `130.125` Igualada: `123.175` Sabadell: `120.800`

### Baixells

- <https://blog.escolaport.com/canales-marinos-vhf-frecuencias-y-tabla/>

## Atacs a claus de cotxes

Realitzarem un atac anomenat Replay Attack, que bàsicament consta de llegir una senyal i tornar-la a emetre.

Tanmateix ho farem pas a pas per entendre el procés, veure com analitzar les senyals per determinar si són vulnerables al atac simple, entendre possibles mesures de seguretat i propossar atacs més avançats per sortejar-les.

### Captura

1. Trobar la senyal

   Programa Gqrx (en linux). Aprop dels 433MHz. ¿AM? AMb GQRX, secció Rec.
   ![[IC10/0226/RA4/Pasted image 20260410095904.png]]

### Comparació senyals

Amb audacity

1. Senyals simples\
   ![[IC10/0226/RA4/Pasted image 20260410095921.png]]

2. Claus rotatories (Key rolling)\
   ![[IC10/0226/RA4/Pasted image 20260410095933.png]]

3. Atac de repetició

   Amb GNURadio

   1. Atac de repetició

   2. Atac de repetició + jamming

      Realitzarem un atac anomenat Replay Attack, que bàsicament consta de llegir una senyal i tornar-la a emetre.

      Tanmateix ho farem pas a pas per entendre el procés, veure com analitzar les senyals per determinar si són vulnerables al atac simple, entendre possibles mesures de seguretat i propossar atacs més avançats per sortejar-les.

## Coses de l'estat i serveis d'emergència

Utilitzen TETRA.

### Mossos

- TETRA codificat.
- Tot i això es pot identificar l'emisor i geolocalitzar-lo.

### Emergències

- TETRA sense codificar.
- SEM: `390.610` 390.435 390.185 390.580 390.800 390.400 390.630 390.985

## Tempest

<https://www.youtube.com/watch?v=HkdoKIo5eno>

## Senyals a investigar

#### 3.6.1. 150.000

![RADIO150000.png](https://lacetanica.cat/apunts/SMX/MP06/UF5/RADIO150000.png)

#### 3.6.2. 158.400

#### 3.6.3. 164.350

# NFC

# RFID

# Bluetooth
