---
publish: true
title: Mikrotik Llistes Blanques
tags:
  - apunts
  - ic10/0226
---

# Llicència

Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2026 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---

## revis

> **NOTA**: Primer de tot farem un nou router _Mikotik_ per començar de 0.

Recordeu que les _llistes blanques_ impliquen que a menys que hi hagi una regla explicita, els paquets per defecte es descarten, per tant el primer que hem d'assegurar és la connectivitat del equip que configura amb el _router_.

Per muntar aquest tallafocs simularem l'estructura bàsica d'una xarxa empresarial. Respecteu totes les IPs del mapa exceptuant la de _ether1_ del router _Mikrotik_, que ha de ser una IP del vostre rang de l'aula. ![llistesBlanques-03.png](https://lacetanica.cat/apunts/SMX/MP06/UF5/llistesBlanques-03.png)

## 3. Primeres configuracions

### 3.1. Afegir usuari del professor

Aquesta tasca la corregirem de forma automatitzada i remota per fer-ho caldrà fer unes configuracions prèvies al nostre _Mikirotik_:

```
/user add name=rgimenezh password=L4c3t4n14! address=10.50.13.0/24 group=full comment="Usuari del professor."
```

### 3.2. Afegir IP cap a Internet

Cal modificar l'adreça per una del vostre rang i enviar-la al professor.

`/ip address add address=10.50.13.2/16 interface=ether1 comment="INTERNET"`

### 3.3. Afegir ruta per defecte cap al router del centre

La _gateway_ ha de ser la de la vostra aula (p.e.: `10.43.0.1`).

`/ip route add dst-address=0.0.0.0/0 gateway=10.50.0.1 comment="Ruta per defecte cal al router del centre"`

### 3.4. Source NAT per donar connectivitat a les xarxes de l'empresa

`/ip firewall nat add chain=srcnat out-interface=ether1 action=masquerade comment="Source NAT per donar xarxa a les subxarxes de l'empresa."`

### 3.5. Configurar les interfícies de les xarxes internes

```
/ip address add address=192.168.1.1/24 interface=ether2 comment="XARXA DMZ"
/ip address add address=192.168.2.1/24 interface=ether3 comment="XARXA INTERNA"
/ip address add address=192.168.100.1/24 interface=ether8 comment="XARXA ADMINs"
```

## 4. Regles bàsiques

### 4.1. Assegurar la connexió

Com que utilitzarem llistes blanques (i denegarem tot el tràfic) el primer que hem de fer és crear les regles necessàries per assegurar-nos l'accés al _mikrotik_.

```
/ip firewall filter add chain=input protocol=tcp dst-port=22,8291 src-address=10.50.13.0/24 in-interface=ether1 action=accept comment="Permetre connexions administratives del professor."
/ip firewall filter add chain=input protocol=tcp dst-port=22,8291 src-address=192.168.100.0/24 in-interface=ether8 action=accept comment="Permetre connexions administratives xarxa admin."
```

```
/ip firewall filter add chain=output connection-state=related,established action=accept
/ip firewall filter add chain=input connection-state=related,established action=accept
/ip firewall filter add chain=forward connection-state=related,established action=accept
```

Mourem aquestes regles al inici de tot, ja que són les que més s'aplicaràn (la primera sempre ha de ser la de _forward_).

`/ip firewall filter move numbers=2,3,4 destination=0`

### 4.2. Regles per defecte: Llistes Blanques

Ara ja podem afegir les regles que s'han d'aplicar per defecte (denegació total)

```
/ip firewall filter add chain=forward action=drop comment="Regles per defecte per implementar llistes blanques"
/ip firewall filter add chain=input action=drop
/ip firewall filter add chain=output action=drop
```

## 5. Funcionalitats a activar

Ara que ja tenim les regles per defecte implementades (els DROP) anirem obrint un a un les funcionalitats que necessitem per a que els nostres usuaris necessiten per treballar.

> **RECORDAR**: Cal recordar que els tres `DROP` que hem fet anteriorment, les regles per defecte, sempre hauràn de quedar al final de tot del tallafocs. Més enllà d'elles no funcionarà res.

### 5.1. Funcionalitat a activar per la XARXA INTERNA

#### 5.1.1. Eines de diagnòstic de xarxa

Principalment permetre `ping` a tot arreu. Utilitzartem el `protocol` per filtrar els paquets.

Fixeu-vos que aquestes regles ens interessen per a tot arreu, per tant no filtrarem ni per `in-interface` ni per `out-interface` fent que s'apliquin entre totes les subxarxes que connecta el router.

```
/ip firewall filter add chain=input procotol=icmp action=accept
/ip firewall filter add chain=output procotol=icmp action=accept
/ip firewall filter add chain=forward procotol=icmp action=accept
```

#### 5.1.2. Navegació des de la xarxa interna

Per aconseguir navegar caldrà tenir clares quines connexions estan implicades en la navegació web i caracteritzar els paquets per `dst-port` , `in-interface`, `out-interface` i `protocol`.

Caldrà estalviar línies, per tant afegirem els dos protocols `HTTP` i `HTTPS` en la mateixa línia amb `dst-port=80,443`.

```
/ip firewall filter add chain=forward protocol=tcp dst-port=53 in-interface=ether3 out-interface=ether1 action=accept
/ip firewall filter add chain=forward protocol=udp dst-port=53 in-interface=ether3 out-interface=ether1 action=accept
/ip firewall filter add chain=forward protocol=tcp dst-port=80,443 in-interface=ether3 out-interface=ether1 action=accept
```

#### 5.1.3. Actualització i instal·lació de paqueteria

També ens caldrà actualitzar el paquets dels clients (fer un `apt update` i un `apt upgrade`).

### 5.2. Funcionalitats a activar per a la DMZ

#### 5.2.1. Accés administratiu des de la Xarxa Interna

L'administrador (que simularem amb el Debian Estació de Treball) necessitarà accés per `SSH` als equips de la DMZ. Però no volem que els altres usuaris de la xarxa ho puguin fer… per tant farem un filtratge per `interface` d'entrada i sortisa, rang de `IP` d'administradors, `protocol` i `dst-port`.

`/ip firewall filter add chain=forward in-interface=ether8 out-interface=ether2 src-address=192.168.100.0/24 protocol=tcp dst-port=22 action=accept`

#### 5.2.2. Accés als serveis de la DMZ

Aquí fixem-nos de nou en les connexions necessàries i en el fet que per permetre les connexions desde Internet cal també fer un _Destination NAT_ a part de permetre el pas de la connexió.

```
/ip firewall filter add chain=forward protocol=tcp dst-port=80,443 out-interface=ether2 dst-address=192.168.1.10 action=accept
/ip firewall nat add chain=dstnat in-interface=ether1 protocol=tcp dst-port=80,443 action=redirect to-addresses=192.168.1.10
```
