---
publish: true
tags:
  - apunts
---

# Llicència

Aquest document es publica sota llicència **[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)**

**2025 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[![[Meta/Plantilles/buymeacoffee.png]]](https://ko-fi.com/raulgimenezherrada)

---

# IC10-0226-RA3 Activitat HIDS amb OSSEC

Algunes de les característiques de OSSEC:

- Active response- responds to attacks in real time using various mechanisms.
- Rootkit and malware detection
- Log based intrusion detection- it monitors and analyses data in real time.
- System inventory-collects the system’s information such as the software, hardware network services e.t.c
- File integrity monitoring(FIM)- maintains forensic copy of the data as it changes.
- Compliance auditing- it audits the system and application for compliance with common standards such as PCI-DSS and CIS benchmarks.

## Instal·lació de OSSEC

Actaulització del sistema

apt update && apt upgrade -y && apt auto-remove -y

Instal·lació de pre-requisits / dependències.

apt -y install  wget git vim unzip make gcc build-essential php php-cli php-common libapache2-mod-php apache2-utils inotify-tools libpcre2-dev zlib1g-dev  libz-dev libssl-dev libevent-dev build-essential libsystemd-dev

Des la [web de descàrregues oficial](https://www.ossec.net/download-ossec/) descarregarem l'última versió, en el cas d'aquest tutorial la `3.7.0` del `OSSEC Server/Agent Unnix`. Tot seguir descomprimirem el `tar` i entrarem en el directori generat.

wget https://github.com/ossec/ossec-hids/archive/3.7.0.tar.gz
tar xvzf 3.7.0.tar.gz
cd ossec-hids-3.7.0

Llançarem l'instal·lador:

sh install.sh

I a partrid aquí anirem seguint els passos de l'assistent d'instal·lació.

**PAS 1**: Tria del idioma, en el nostre cas `es`.

![[IC10/0226/RA3/OSSEC_Idioma.png]]

Després ens informa que instal·larem OSSEC. Premem `ENTER`.

![[IC10/0226/RA3/OSSEC_Confirmacio.png]]

El següent pas és triar el tipus d'instal·lació, en el nostre cas `local` ja que així instal·larem tant l'agent com el servidor en el mateix equip.

![[IC10/0226/RA3/OSSEC_Local.png]]

Ruta per defecte `/var/ossec/` ja està OK, així que premem `ENTER`.

![[IC10/0226/RA3/OSSEC_PuntInstalacio.png]]

Ens demana si volem activar les notificaicons per correu electrònic, per defecte \[s] per tant premem `ENTER`. Després ens demanarà el correu electrònic dos cops i ens detectarà un servidor SMTP de Google que podrem utilitzar. Tanmateix per a que funcioni caldría configurar un servidor `postfix` en local per enviar l'alerta, això ja ho sabeu fer de M7.

![[IC10/0226/RA3/OSSEC_NotificacionsCorreu.png]]

Després ens demanarà si volem activar un parell de monitoritzacions més, lògicament triem l'opció per defecte en tots dos casos que és \[s].

![[IC10/0226/RA3/OSSEC_ActivarDeteccions.png]]

També ens demana si volem que pugui agregar regles al tallafocs, l'hi indiquem que si. ![OSSEC\_Firewall.png](file:///home/rgimenezh/Escriptori/lacetanica/apunts/SMX/MP06/UF4/OSSEC_Firewall.png)

Finalment ens mostra un llistat de IPs que considera segures i ens demana si en volem afegir més. Aquestes IPs es consideraràn segures i per tant no s'activaràn alarmes relacionades amb elles.

![[IC10/0226/RA3/OSSEC_IPsLlistaBlanca.png]]

Per acabar, una petit text de com configurar algunes coses més de forma manual i una confirmació per començar a insta·lar-ho tot.

![[IC10/0226/RA3/OSSEC_ConfirmacioFinal.png]]!

Un cop tot instal·lat, ens dona missatge de finalització junt amb instruccions de com arrencar i parar el servei alhora de com modificar-ne la configuració.

![[IC10/0226/RA3/OSSEC_Finalitzacio.png]]

## Inicialitzar OSSEC

/var/ossec/bin/ossec-control start

Podem veure les alertes de forma manual al directori

cat /var/ossec/logs/alerts/alerts.log

## Verificació del funcionament

Per verificar el bon funcionament de OSSEC farem, des d'un altre màquina un SSH tot equivocant-nos d'usuari i/o contrasenya. Un cop fet veurem que la reacció de OSSEC ha bloquejar la IP mitjançant `iptables` (recordeu que ho podem veure amb la comanda `iptables -S`) i generar una alerta que trobarem a `/var/ossec/logs/alerts/alerts.log`.

![[IC10/0226/RA3/OSSEC_RespostaActiva.png]]

![[IC10/0226/RA3/OSSEC_AlertaSSH.png]]

# Webgrafia

- <https://techviewleo.com/install-and-configure-ossec-hids-agent-on-debian/>
- <https://github.com/ossec/ossec-hids/issues/2039>

# Flipped class

![Flipped Class](https://www.youtube.com/watch?v=8qksSowfS1k)
