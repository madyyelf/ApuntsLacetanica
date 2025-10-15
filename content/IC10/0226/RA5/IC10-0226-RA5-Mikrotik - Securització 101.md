---
{"publish":true,"title":"Mikrotik - Securització 101","tags":["apunts","ic10/0226"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2025 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---
# Mikrotik - Securització 101
## Motivació

Quan instal·lem un nou equipament, com un enrutador, cal assegurar-nos des del primer moment que l'hi **apliquem unes mínimes mesures de seguretat**. És especialment **important** en equipaments que formin part de la **xarxa perimetral** i la recomanació és **assegurar-los abans de connectar-los a Internet** per evitar que puguin ser atacats abans de que els tinguem configurats.

Depenent de l'element tindrem uns paràmetres o altres, en el cas d'un enrutador _Mikrotik_ les recomanacions són les següents:

## Abans de connectar-ho a Internet

Com hem comentat anteriorment, en connectar el router a Internet el que estem fent és expossar-lo i arriscar-nos a un atac. Això **no ho hem de fer amb el router sense configurar** ja que, per exemple, encara tindrà el **usuari i contrasenyes per defecte** i per tant ens poden entrar molt fàcilment amb eines automàtiques.

Com sempre, tindrem al cap **minimitzar la superfície d'atac** al router, reduint i controlant **qui** pot accedir, **com** (serveis) i **des-de on**.

Per tant, **abans de connectar el router a Internet** cal configurar alguns aspectes com poden ser:

### Usuaris

El primer pas és gestionar correctament els usuaris que poden accedir al _Mikrotik_.

#### Crear nou usuari administrador

Al crear un nou usuari, dificultem la tasca dels atacants, ja que han d'esbrinar tant l'usuari del sistema com la contrasenya.
```
/user add name=rgimenezh password=L4c3t4n14! group=full
```
#### Eliminar usuari `admin`

En eliminar l'usuari `admin` (l'usuari per defecte) estem impedint que puguin utilitzar l'únic usuari que a priori un atacant pot conèixer d'avant-mà.
```
/user remove admin
```
#### Limitar l'accés de l'usuari des de una IP o rang

Si restringim des de quines IPs pot fer login un usuari al _Mikrotik_, ens assegurem que tan sols es pugui entrar des de màquines concretes (administrador) o xarxes concretes (xarxa d'administradors). Impedirem doncs connexions des de l'exterior i fins i tot, en el cas d'un atac amb origen intern, des de xarxes pròpies no tan confiables.
```
/user set rgimenezh address = 192.168.0.2
```
### Serveis

El segon punt crític és minimitzar els serveis oferts i com es pot accedir a ells.

Listing 1: Comanda per llistar els serveis que ofereix el router Mikrotik.
```
/ip service print
```
#### Eliminar serveis innecessaris
```
/ip service disable telnet,ftp,www,api,api-ssl
/ip service print
```
#### Ofuscació del servidor SSH
```
/ip service set ssh port=2200
/ip service print
```
#### Restringir L'accés dels serveis a IPs o rands
```
/ip service set winbox address=192.168.88.0/24
```
### Accés per MAC
```
/tool mac-server set allowed-interface-list=ether8
/tool mac-server mac-winbox set allowed-interface-list=ether8
/tool mac-server ping set enabled=no
/tool mac-server print
```
### Discovery
```
/ip neighbor discovery-settings set discover-interface-list=ether8
```
### Altres mesures variades
```
/tool bandwidth-server set enabled=no
/ip dns set allow-remote-requests=no
/ip ssh set strong-crypto=yes
```
## Un cop connectat a Internet

### Actualització del sistema

## Webgrafía

- [https://wiki.mikrotik.com/Manual:Securing_Your_Router](https://wiki.mikrotik.com/Manual:Securing_Your_Router)