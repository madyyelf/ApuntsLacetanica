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

La idea final del treball és que acabeu amb l'estructura típicament utilitzada a les empreses de una DMZ per a serveis externs i com a mínim una subxarxa per als equips de producció.

![[IC10/0226/RA4/winbox.png]]

Aquest és un esquema molt bàsic a partir del qual podem créixer a com a xarxa, creant una subxarxa de servidors interns, afegint *Access Points*, subxarxes per finalitats concretes com per exemple taller informàtic, etc.

## Equips Host
Podeu crear dos *màquines virtuals* noves, una que contingui un servidor web (afegiu una web personalitzada, tan sols HTML) i un client que pot ser un Debian amb entorn gràfic per a que ocupi menys espai.  Si no voleu crear les màquines, aquí us facilito un parell de OVAs ja fetes (tot i que desactualitzades). 
- [Servidor Web (Xarxa DMZ)](https://drive.google.com/file/d/19Y5heiovU5Eujz1VugDzA7HlwwfAzttv/view?usp=drive_link).
- [Debian Client GUI (Xarxa Interna)](https://drive.google.com/file/d/1QW6Z2HJgWe9SM1r9DzDbEMlDJW6jnnB-/view?usp=drive_link).

## Switchos i xarxa física
Un cop fet això haurem de simular els dos *switchos*, si ho feu amb GNS3 ja sabeu com fer-ho.  A *VirtualBox*, a la màquina del router *Miktorik* anirem al mení `Xarxa->Adaptador 2-> Attached To` i triarem `Xarxa Interna`, a la opció `Name` hi configurarem `DMZ`.  Això el que crea és un "*switch*" virtual on totes les màquines que configurem d'aquesta forma l'adaptador de xarxa estaràn virtualment conectades entre si.

Repetirem l'operació per al `Adaptador 3` i en aquest cas el nom de la xarxa serà `INTERNA`.

Ara farem el mateix amb les màquines virtuals del `SRV-WEB` , connectant-lo al *switch* de la `DMZ`i la màquina `DEBIAN-CLIENT` connectant-la al *switch* de `INTERNA`.

Un cop fet això ja tindrem la part física de l'esquema de xarxa que hem planificat a l'imatge inicial de l'activitat.  Ens queda configurar les xarxes de tots els equips per a que es vegin entre ells.
# Treballant de forma real

Per treballar de forma real, hem de ser conscient que no podríem "obrir un terminal" al router _Mikrotik_, per tant simularem una última màquina virtual (podeu utilitzar qualsevol) on simularem el portàtil del administrador que gestiona el router mitjançant un port d'administració `ether8`.   Si el vostre ordinador no suporta bé quatre màquines virtuals funcionant, utilitzeu la interfície gràfica del propi router, tot i que cal deixar clar que en la realitat això no es pot fer.

Un cop tingueu aquest PC amb `winbox`, busqueu el router per `MAC` i connecteu-vos.  Fixeu-vos que treballant per `MAC`no ens cal configurar cap mena de `IP`ni al router ni al PC que conté `winbox`.
## Xarxa externa

Aquesta és la subxarxa que simularà Internet i la connexió amb el nostre ISP.

- Primer interfície de `Virtual Box` configurada com `Adaptador Pont`.
- Al `ether5` (el del numeral més baix) del _Mikrotik_.
- IP estàtica dins del vostre rang (en el meu cas `10.50.13.31/16`) i la _gateway_ corresponent (en el meu cas `10.50.0.1`).
## Xarxa DMZ
Aquí hi connectarem els servidors que donin serveis externs, com el _email_ o _pàgina web_.

- A `Virtual Box`  del `Mikrotik` ha de ser la segona interfície, configurada com a `Xarxa Interna` i nom de xarxa `DMZ`.
- Al `ether6` (el segon més baix) del `Mikrotik`.
- IP estàtica: `192.168.1.1/24`.
- Configurar xarxa de la màquina `SRV-WEB` amb `192.168.1.10/24` i _gateway_ `192.168.1.1`.  Al seu `Virtual Box` ha de tenir la primera interfície configurada com a `Xarxa Interna` i nom de xarxa `DMZ`.

## Xarxa Interna
Aquí hi connectarem tots els equips de treball de l'empresa, com per exemple _estacions de treball_, _impressores_, _Servidor de Active Directory_, _Servidors d'arxius_, etc.

 A `Virtual Box`  del `Mikrotik` ha de ser la tercera interfície, configurada com a `Xarxa Interna` i nom de xarxa `INTERNA`.
- Al `ether7` (el segon més baix) del `Mikrotik`.
- IP estàtica: `192.168.2.1/24`.
- Configurar xarxa de la màquina `SRV-WEB` amb `192.168.2.10/24` i _gateway_ `192.168.1.1`.  Al seu `Virtual Box` ha de tenir la primera interfície configurada com a `Xarxa Interna` i nom de xarxa `INTERNA`.
# Dotar d'Internet a tota la xarxa
Per donar connectivitat a Internet a tota la xarxa haurem de fer dues passes.
## Gateway al router
Primer de tot cal establir la ruta per defecte del router, cap al router de l'institut amb la comanda `ip route add dst-address=0.0.0.0.0/0 gateway=10.50.0.1`. Heu de substituir `10.50.0.1`per la gateway corresponent a la vostra aula.
## SRC-NAT
Cal també fer que el router modifiqui la IP d'origen dels paquets provinents de les xarxes internes i que surten cap a Internet.  Això ho aconseguim així:
`ip firewall nat add chain=srcnat out-interface=ether5 action=masquerade`
Com en els passos anteirors caldrà que modifiqueu la `out-interface`per la corresponent en el vostre router que connecta amb la xarxa de l'aula.
# Verificacions

Cal verificar la connectivitat entre elements de la mateixa xarxa. Per tant des del Mikrotik haurem de fer ping

- `ping 8.8.8.8` per verificar connexió amb Internet i xarxa local del centre. Si falla repassar configuració `eth1`.
- `ping 192.168.1.10` per verificar connexió xarxa DMZ. Si falla repassar configuració `eth2`.
- `ping 192.168.2.10` per verificar connexió xarxa DMZ. Si falla repassar configuració `eth3`.
- `ping 8.8.8.8` desde qualsevol màquina de la xarxa (servidor web o client).
