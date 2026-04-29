---
{"publish":true,"title":"Anàlisi de Phishing","tags":["apunts","ic10/0226"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2026 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---
Analitzar un correu maliciós ens pot servir per molts propòsits.

- Conneixer les tècniques que utilitzen els agents maliciosos.
- Detectar si som víctimes d'un atac indiscriminat o d'un atac dirigit cap a nosaltres.
- Conneixer les motivacions i objectius dels agents maliciosos.
- Entendre l'infraestructura utilitzada pels atacants.

A part de coneixement bàsic sobre l'atac concret aquest anàlisi ens pot ajudar també a **crear mesures de seguretat** (_indicadors de compromís_, regles de tallafocs, antivirus o IDS) per detectar futurs atacs, saber o detectar si algun equip de la nostra xarxa ha estat víctima o fins i tot fer seguiment de la campanya i intentar atribuïr-la a un dels grups de hacking actius en el panorama actual.

Per tant aquesta tasca, si es realitza amb consciencia, ens donarà una vagatge important en matèria de cyberseguretat, resposta a incidents i anàlisi forense.

## 1. Recuperació de evidències

Per recuperar el email a analitzar és important que MAI l'obrim en una màquina normal. Per tant el que podem fer des de GMail per exemple es **reeviar-nos els emails com adjunts**, sense arribar a obrir-los mai.


![[IC10/0226/RA4/re-enviar_phishing.gif]]
Figure 1: Així es pot obtenir el original del correu, sense obrir-lo i per tant sense infectar-se.

## 2. Anàlisi dels correus

Obrim els arxius que ens hem enviat com adjunts, utiltizant un editor de textos plans com `vi`, `nano`, `wordpad`, etc.

Analitzarem varis punts del correu.

### 2.1. Capçaleres Received

Aquestes capçaleres **enregistren el pas entre servidors** de correu electrònic del email. D'aquesta manera es pot intentar fer una traçabilitat fins l'origen del correu.

Típicament ens trobarem amb dos casos:

#### 2.1.1. L'origen és un WebMail

L'origen del paquet acaba resultant un servei de Webmail (com gmail) i per tant no podem saber qui l'ha enviat. **Caldria una ordre judicidal** (prèvia demanda) per aconseguir els registres dels servidors.

Received: by mail-pl1-x633.google.com with SMTP id r8so4281870pls.2
        for <raul.gimenez@lacetania.cat>; Mon, 30 Jan 2023 02:38:08 -0800 (PST)

#### 2.1.2. IP Privada

Aconseguim la IP d'un equip privat. Aquesta IP podría correspondre a veritable atacant, però és **probable que sigui un ordinador pr-eviament infectat** i controlat per l'atacant. Podriem analitzar-ho amb Shodan i intentar extreure conclusions.

Received: from huawei-sim.com (huawei-sim.com. [14.192.50.48])
        by mx.google.com with ESMTP id a9-20020a170902ecc900b0019515ca627fsi3387285plh.422.2023.01.24.11.55.31
        for <madyyelf@gmail.com>;
        Tue, 24 Jan 2023 11:55:32 -0800 (PST)

Un cop aquí podem avançar mirant a qui pertany la IP trobada, utiltizant un servei de [WhoIs](https://who.is), i **analitzar-la a fons**.

![[IC10/0226/RA4/Pasted image 20260421180812.png]]

Figure 2: Aquest IP en concret pertany a un ISP d'àsia. Per tant sembla el PC d'un particular o d'una empresa.

També podem utilitzar un escàner de ports com `nmap` o simplement Shodan (previ registre) per analitzar aquesta IP i **fer-nos una idea de si pot ser l'atacant real o un ordinador infectat**.

![[phishing_shodan.gif]]

Figure 3: El equip realment està ple de vulnerabilitats, per tant és molt probable que estigui sent utilitzat per un atacant remot.

### 2.2. Content-Type

El contingut d'un email queda reflectit en les capçaleres `content-type`. Per tant per saber **què conté realment un email** haurem de donar-hi un cop a aquestes capçaleres.

Text/ PLAIN o HTML

Multipart

El correu conté diferents tipus de continguts, separats. Per tant caldrà detectar les marques de separacions i el `Content-type` de cada part. És el típic correu amb adjunts (`mixed`) o diferents formes de visualitzar-se (`alternative`). Els més complexos i per tant força utilitzats per encavir-hi malware.

Application/*, audio/*, image/*, video/*

Contingut multimèdia adjunt que normalment es visualitza com adjunt. Si en trobem caldrà anlitzar-los apart (no entrarem en aquest treball).

### 2.3. Contingut del email

Dins el contingut del correu ens fixarem en diferents apartats:

#### 2.3.1. Enllaços

Potser la part més interessant d'analitzar ja que aquí trobarem tant les tècniques com els objectius del correu _phishing_. Coses interessants a analitzar poden ser:

- **Servidor o domini objectiu**: Analitzarem el domini objectiu per determinar si és un lloc web real, una IP privada o un domini que s'hagi utilitzat alguna tècnica d'enmascarament. De nou podem **utilitzar _Shodan_ o _NMap_** per analitzar aquest nou element. També analitzarem com és el domini, i en el cas que s'estiguint fent passar per algú altre quina tècnica utilitzen (tlktok.com, tècniques de [IDN homograph attakcs](https://en.wikipedia.org/wiki/IDN_homograph_attack), etc…).
- **Enllaços**: Normalment tots els enllaços apuntaràn al mateix lloc, ja que es centralitza l'atac, però cal verificar-los tots un a un.
- **Contingut del lloc enllaçat**: Obrirem els enllaços **des d'una màquina virtual neta** (sense dades personals), visitarem i analitzarem el lloc on ens porten (que ens demanen, si hi ha javascript, etc) i finalment eliminarem la màquina virtual per evitar derivades d'una infecció.
- També utilitzeu la web de [https://www.virustotal.com](https://www.virustotal.com) per analitzar la web (URL), podent detectar atacs.
- Les URLs i dominis que han desaparegut (ja no són funcionals) podem encara donar un cop d'ull per veure com eren des de la web de [https://www.waybackmachine.com](https://www.waybackmachine.com).

#### 2.3.2. JavaScript i altres llenguatges de la banda del client

Normalment els correus **es visualitzen com _HTML_** i per tant s'hi poden incloure qualsevol llenguatge que sigui interpretat per un navegador web. Això inclou llenguatges de programació de la banda del client com _Javascript_. Per tant cal repassar si existeix alguna etiqueta `<script>` on funcions amagades en events del codi _html_ com per exemple `onmouseover=`. Aquests codis **s'executarien automàticament en obrir el correu**, tanmateix normalment aquests **llenguatges ja contenten salvaguardes** per evitar que es s'executin accions realment perilloses com execució d'arxius, etc.

#### 2.3.3. Tècniques per evadir sistemes anti-spam

El correu maliciós acostuma a utilitzar tècniques per evadir els sistemes antispam, com per exemple text ocult, codificació base64 o comentaris _html_ **per mutar-se i intentar passar desaparçebut**. De vegades podrem veure contingut que simula contingut "normal" per aconseguir que el email obtingui millor puntuació en els sistemes de detecció de _spam_, o contingut xifrat, etc. D'altres, aquest contingut ocult pot servir com a marques per a afinar una campanya més complexa, etc…

#### 2.3.4. Carteres de bitcoins

A vegades, especialment en els programes ramsonware però també en algunes campanyes de phishing, podem trobar carteres de bitcoins on els agents maliciosos ens demanen que ingressem una quantitat de calers. Pot ser interessant veure els **moviments monetaris** d'aquestes cateres (que són totalment públics) per fer-nos una idea del moviment del compte i si les quantitats coincideixen en el que apareix en l'email analitzat.

#### 2.3.5. Adjunts

Vigilem molt en els adjunts, tan sols obrir-los en màquines virtuals!

- [Virus Total](https://www.virustotal.com/gui/): Aquí el podem enviar i que l'analitzin per veure si pot contenir virus.
- [ANY.RUN](https://any.run/): És un sandbox on durant 1 minut podrem interactuar amb una VM i es registrarà tota l'activitat feta, poden veure activitat maliciosa de forma segura.

Donada la complexitat d'analitzar un adjunt, no farem més proves per risc a infectar-nos!

Podem consultar aquests moviments cercant el número de la cartera a [BlockChain.com](https://www.blockchain.com/en/wallet).

![[IC10/0226/RA4/phishing_wallet.gif]]

Figure 4: LA cerca d'una cartera de bitcoins, el contingut i les seves transaccions.

## 3. Exemple

El email d'exemple és un correu que em va arribar a mi a la "_bandeja d'entrada_" i que utilitza vàries tècniques tant psicològiques com informàtiques que són interessants de analitzar.

### 3.1. Capçaleres Recived

La **última capçalera** ens mostra que el correu electrònic **prové de _rsmail.alkoholic.net_** que a dia d'avuí ha desaparegut, el mateix que la IP.

![[IC10/0226/RA4/Pasted image 20260421180916.png]]

Figure 5: Capçaleres del correu, és un domini desaparegut, però encara podem investigar més a fons amb WayBackMachine…

Tanmateix podem utilizar [waybackmachine](https://web.archive.org/web/20230000000000*/alkoholic.net) per veure què hi habia antigament en aquest domini i podem veure que **va desapareixer el octubre del 2022**, i tenia aquesta pinta… tota la pinta de haber estat **hackejada**…

![[IC10/0226/RA4/Pasted image 20260421180927.png]]

Figure 6: Amb WayBackMachine podem veure que va desapareixer el domini el 2022 i que, per la pinta que tenia, possiblement habia estat hackejada.

### 3.2. Content-Type

Com podem veure és `text-html`, tanmateix està **codificat en base64**.

![[IC10/0226/RA4/Pasted image 20260421180953.png]]

 Aquesta codificació segurament s'està utilitzant com a **tècnica per evadir els sistemes anti-spam**. Si decodifiquem el base64 amb [aquest enllaç](https://www.base64decode.org/) obtenim el contingut del correu en text/html.

### 3.3. Contingut del correu

Dins del contingut cal destacar ràpidament:

- L'ús del **nom d'usuari** de la víctima.
- L'ús d'una **contrasenya** de la víctima, antiga, que segurament el hacker ha obtingut d'algun [filtratge prèvi](https://haveibeenpwned.com/).

![[IC10/0226/RA4/Pasted image 20260421181006.png]]

Figure 7: Ens donen dades personals per imprimir veracitat a l'atac i que creguem que realment ens han entrat.

Tot això s'utilitza per a **aconseguir imprimir veracitat** a l'atac.

![[IC10/0226/RA4/Pasted image 20260421181018.png]]

Figure 8: Utilitzen la por i la vergonya social per a forçar-nos i que actuem de forma irracional, pagant el rescat.

També veiem que intenta fer veure que **ens ha instal·lat un programa de vigilància i ens ha pillat mirant porno**, cosa que segurament farà una part molt important de les víctimes, i ens **amenaça amb difondre el vídeo** al nostres contactes. Aquí **ens inculten por** i ens fan **chantatge** demanant-nos uns 900€ en bitcoins, el rerefons de l'atac.

![[IC10/0226/RA4/Pasted image 20260421181040.png]]

Figure 9: El contingut HTML també conté text ocult, de color blanc, segurament per evadir de nou sistemes anti-spam.

També crida l'antenció en el codi HTML que hi han varis **textos de color blanc**, principalment el nom d'usuari, el password i textos que semblen random. Segurament de nou es tracta d'una **tècnica d'evasió de sistemes anti-spam**.

![[IC10/0226/RA4/Pasted image 20260421181051.png]]

Figure 10: Finalment ens trobem amb una adreça d'una cartera de bitcoins, on podem veure algunes de les transaccions realitzades durant el perïode de la campanya de phishing.

Per acabar ens trobem amb una **cartera de bitcoins**, que podem [analitzar a _BlockChain_](https://www.blockchain.com/explorer/addresses/btc/1ELzee2T9Wd5YPTYhWbWD3xK7xB5tJ94J4) i veure que aquesta cartera realment va tenir **molt moviment**, possiblement d'altres campanyes de phishing, però **poc ingressos coincideixen** amb la xifra que ens demana a nosaltres.

### 3.4. Conclusions

Aquesta sembla ser una campanya de phishing on han utilitzat les dades de nom d'usuari, email i password d'algun filtratge anterior per a fer l'enviament a les víctimes i utilitzar aquesta informació per donar pes i veracitat al chantatge. A partir d'aquí fan chantatge utilitzant la por de l'escarni públic amenaçant d'enviar un vídeo on la víctima apareix "mirant porno" a tots els seus contactes. Per evitar-ho tan sols cal que pagui uns 900€ a una cartera de bitcoins. Per tant l'objectiu últim d'aquesta campanya és el guany econòmic directe mitjançant el chantatge.

A nivell tècnic hem vist que han utilitzat un servidor prèviament hackejat per a fer l'enviament del phishing i que han utilitzat codificació en base64 del contingut del correu i textos ocults per a intentar dificultar les tasques dels sistemes anti-spam i aconseguir que el correu aparegues a la safata d'entrada de la víctima.

Finalment analitzant la cartera de bitcoins veiem que tot i que els imports no coincideixen exactament amb els de la campanya de phishing analitzada, aquesta cartera ha tingut molt moviment durant el periode de la campanya. Tot plegat fa pensar que es tracta no d'una campanya aïllada sinó que forma part d'una activitat criminal molt més amplia i ben organitzada.