---
{"publish":true,"title":"Tallafocs","tags":["apunts"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2025 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---
# Tallafocs
---
## Concepte

Programari que controla paquets entrada / sortida

- Paquets que poden o no poden passar.
- Regular velocitats.
- Distribuïr tràfic.
- Aturar atacs específics.

Controlen el pas entre xarxes diferents o un host.

---
## Tipus

### Implementació

- Software
- Hardware dedicat
---
### Que controlen

- Pas entre xarxes (tallafocs de xarxa)
- Pas a un host (tallafocs de host)
---
### Capes OSI on actuen

  
| CAPA | NOM             | PROTOCOLS                    |
| ---- | --------------- | ---------------------------- |
| 7    | Aplicació       | HTTP,FTP,DNS,SNMP,Telnet,etc |
| 6    | Presentació     | SSL, TLS                     |
| 5    | Sessió          | NetBios, PPTP                |
| 4    | Transport       | TCP, UDP                     |
| 3    | Xarxa           | IP, ARP, ICMP,IPSec          |
| 2    | Enllaç de dades | PPP, ATN, Ethernet (MAC)     |
| 1    | Física          | Impulsos                     |

---
#### Tallafocs de xarxa

  
| CAPA | NOM             | PROTOCOLS                |
| ---- | --------------- | ------------------------ |
| 5    | Sessió          | NetBios, PPTP            |
| 4    | Transport       | TCP, UDP                 |
| 3    | Xarxa           | IP, ARP, ICMP,IPSec      |
| 2    | Enllaç de dades | PPP, ATN, Ethernet (MAC) |

---
#### Tallafocs d'aplicació

  
| CAPA | NOM         | PROTOCOLS                         |
| ---- | ----------- | --------------------------------- |
| 7    | Aplicació   | HTTP, FTP, DNS, SNMP, Telnet, etc |
| 6    | Presentació | SSL, TLS                          |

---
## Com crear un tallafocs
---
### Llistes negres

Deixem passar tot, excepte el que indiquem a mà.

- El que no coneixem passarà -> Poc segur.
- Fàcil implementar i mantenir.
---
### Llistes blanques

No deixem passar res a menys que ho indiquem a mà.

- Molt control sobre el tràfic -> Molt segur.
- Difícil d'implementar i mantenir.
---
### Forma d'escriure les regles

Es poden escriure mirant d'on ve un paquet, cap a on va, etc.

- Mantenir sempre la mateixa forma d'identificar un paquet.
---
### Control d'entrada i sortida

Controlar el que entra però també el que surt, evitarem mal ús de la xarxa i _malware_.

---
### Manteniment

Cal manteniment periòdic i repàs de logs.

---
## Tallafocs típics
---
### Tallafocs de host

- Windows : El propi
- Linux: iptables -> nftables (tot sobre _netfilter_).
---
### Tallafocs de xarxa

- Linux: Derivats de _netfilter_.
- Fortinet
- Cisco
