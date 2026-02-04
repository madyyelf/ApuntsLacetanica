---
{"publish":true,"title":"Mikrotik DMZ","tags":["apunts","ic10/0226"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2025 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---
# Muntatge
Igual que faríem en una xarxa real, primer de tot assegurarem el router Mikrotik seguint el [[IC10-0226-RA4-Mikrotik - Securització 101 \| document anterior]] i després començarem a muntar l'estructura de la xarxa.

La idea final del treball amb tallafocs és que acabeu amb l'estructura típicament utilitzada a les empreses de una DMZ per a serveis externs i com a mínim una subxarxa per als equips de producció.

![[IC10/0226/RA4/winbox.png]]

Fixeu-vos que en acabar, i de cara el projecte final de síntesi, tan sols caldría afegir les noves VMs que munteu dins de la subxarxa corresponent, i com molt, afegir alguna nova subxarxa depenent del projecte (xarxes wifi, de convidats, de reparació, etc).

## OVAs
- [Servidor Web (Xarxa DMZ)](https://drive.google.com/file/d/19Y5heiovU5Eujz1VugDzA7HlwwfAzttv/view?usp=drive_link).
- [Debian Client GUI (Xarxa Interna)](https://drive.google.com/file/d/1QW6Z2HJgWe9SM1r9DzDbEMlDJW6jnnB-/view?usp=drive_link).

## Treballant de forma real

Per treballar de forma real, hem de ser conscient que no podríem "obrir un terminal" al router _Mikrotik_, per tant simularem amb la _appliance_ de _Winbox_ (la trobareu als repositoris oficials) que ens connectem al router mitjançant un portàtil amb _Winbox_ i des d'aquí treballarem les configuracions del mateix.

Un cop afegida la _appliance_ de _Winbox_, amb botó dret aneu a `Edit Config` i configureu una IP dins del rang de la vostra aula.

Connecteu el _Winbox_ a la interfície `eth8` del _Mikrotik_ que serà la que reservarem per connexions administratives, i intenteu connectar-vos per MAC.
## Xarxa externa

Aquesta és la subxarxa que simularà Internet i la connexió amb el nostre ISP.

- Al `eth1` del _Mikrotik_.
- IP estàtica dins del vostre rang (en el meu cas `10.50.13.31/16`) i la _gateway_ corresponent (en el meu cas `10.50.0.1`).
- Connectat al _núvol_.

## Xarxa DMZ

Aquí hi connectarem els servidors que donin serveis externs, com el _email_ o _pàgina web_.

- Al `eth2` del _Mikrotik_.
- IP estàtica: `192.168.1.1/24`.
- Connectat a un _switch_.
- Al _switch_ també connectar VM _Servidor WEB_ (OVA).
- Configurar xarxa _Servidor WEB_ amb `192.168.1.10/24` i _gateway_ `192.168.1.1`.

## Xarxa Interna

Aquí hi connectarem tots els equips de treball de l'empresa, com per exemple _estacions de treball_, _impressores_, _Servidor de Active Directory_, _Servidors d'arxius_, etc.

- Al `eth3` del _Mikrotik_.
- IP estàtica: `192.168.2.1/24`.
- Connectat a un _switch_.
- Al _switch_ també connectar VM _Client Debina GUI_ (OVA).
- Configurar xarxa del _Client Debian GUI_ amb IP `192.168.2.10/24` i _gateway_ `192.168.2.1`.

# Verificacions

Cal verificar la connectivitat entre elements de la mateixa xarxa. Per tant des del Mikrotik haurem de fer ping

- `ping 8.8.8.8` per verificar connexió amb Internet i xarxa local del centre. Si falla repassar configuració `eth1`.
- `ping 192.168.1.10` per verificar connexió xarxa DMZ. Si falla repassar configuració `eth2`.
- `ping 192.168.2.10` per verificar connexió xarxa DMZ. Si falla repassar configuració `eth3`.