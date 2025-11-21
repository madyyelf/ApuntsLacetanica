---
{"publish":true,"tags":["apunts"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)**

**2025 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[![[Meta/Plantilles/buymeacoffee.png]]](https://ko-fi.com/raulgimenezherrada)

---
# Com detectar una intrusió?

¿Com podem saber si han entrat en els nostres ordinadors?

Realment aquesta és una pregunta molt complicada de respondre. De fet es tracta d'un joc del gat i la rata on mesurar forces amb les del intrús, amb l'inconvenient que mai en podrem estar segurs de que estem lliures d'intrusions, o que realment ens han entrat.

Tanmateix hi han uns quants punts que cal repassar de forma periòdica a la cerca de canvis:

- Usuaris del sistema i els seus permisos.
- Arxius log del sistema i dels serveis.    
- Arxiu Hosts per entrades forçades.    
- Connexions actives (p.e.: amb netstat)    
- Registre de Windows    
- Monitoratge de xarxa en punts crítics (NATs, proxys, etc) a la recerca de tràfic estrany.    

Analitzant tots aquests registres i configuracions podem detectar gran part de les intrusions, ja que en un lloc o altre queden traces de tota activitat.  Al principi serà molt complicat, però a mesura que ens habituem i coneguem el sistema serem capaços de detectar irregularitats de forma ràpida.  A partir d’aquí caldria investigar.

# Software per automatitzar aquestes tasques

Fer tot aquest seguiment de forma manual és una tasca que ens ajudarà a entendre millor el nostre S.I., tanmateix per facilitar-nos la vida també podem recorre a software especialitzat, concretament a detectores d'intrusos (IDS). En podem trobar de dos gustos:

- **HIDS**: Especialment interessant per a servidors i equips "importants", es tracta de Host Intruder Detection System.  Alguns exemples poden ser OSSEC o TripWire.    
- **NIDS**: Si es col·loquen les sondes de forma correcta, aquest tipus de sistemes detectaràn activitat sospitosa en el tràfic de xarxa. Per tant cal col·locar-los en llocs estratègics son sortides, proxys, nats, etc... Alguns exemples poden ser SNORT o SURICATA.
    

També existeixen els anomenats IPS (Intruder Prevention System) que no deixen de ser IDS però amb funcionalitats de resposta més agressives contra l’atacant, el que en la literatura cyberpunk anomenariem Black Ice.

Una tercera eina, que no IDS, és utilitzar paranys per a hackers. Aquests son coneguts com **honey pots** (pots de mel) i és que trobar un servei desprotegit acostuma a ser molt temptador... Si salta l'arma en un d'aquests paranys ens pot donar temps a aixecar l'alerta i preparar la resta de sistemes, aïllar i protegir el vector d'atac, etc.  Tanmateix, més que un sistema de detecció d’intrusos, s’utilitza com a eina d’investigació i aprenentatge ja que podem veure quina és l’activitat del hacker en un entorn segur i així aprendre per lluitar en contra.