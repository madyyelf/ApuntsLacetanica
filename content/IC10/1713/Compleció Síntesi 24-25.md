---
{"publish":true,"tags":["#mentor","apunts","ic10/tutoria"],"cssclasses":""}
---

# Introducció
Aquest projecte és per aquells que no vareu entregar el projecte de síntesi durant el curs 24-25 i voleu fer-ne la compleció. La idea és donar-vos certes parts més pautades, per a que el projecte sigui més clar i no tingueu tants dubtes, a més de donar-vos pautes per a treballar cada apartat alhora que una temporització per a que portar un treball del nivell de qualitat necessari per aprovar sigui factible en el temps que teniu.

**Cal notar que aquest és un document viu i per tant s'anirà treballant i actualitzant de forma regular.  Per tant consulteu l'enllaç per noves versions de forma regular. En qualsevol cas, les activitats i pautes estaran disponibles dins del termini.**
## Projecte
En essencial treballarem els mateixos punts que es treballen en el 90% dels treballs de síntesi presentats fins la data, per tant no és *un treball més fàcil*.  Tanmateix us pautem més cada apartat, traient llibertat i creativitat a canvi de poder-vos guiar una mica més i que sorgeixin menys dubtes.

Tot i seguir aquesta guia, **cal que llegiu també l'enunciat original del treball de síntesi i la resta de materials** relacionats, ja que en ells es donen molts consells i indicacions que també haureu de seguir.
## Seguiment i compromís
Com ja s'ha informat, en el **procés de compleció no hi ha seguiment ni assistència a classes**.  Per tant **cal que sigueu molt autònoms** tant en el treball com en la resolució de dubtes.  Tanmateix alguns professors s'han presentat **voluntaris** per, fora d'hores de feina, fer-vos una mica de seguiment i correcció del treball.

Per aprofitar-ho cal que **entregueu dins dels terminis establerts** les parts pautades i seguiu el ritmen.  **En cas contrari el professorat deixarà de fer-ne seguiment, correccions i resolució de dubtes**.  Seguir i corregir un treball de síntesi suposa molta feina, i si no la podem espaiar no la podrem assumir.  A més, si es deixa per a última hora, es inviable solucionar tots els dubtes que es generin a temps per arribar a l'entrega.
## Resolució de dubtes
Cal recordar que el procediment de compleció no dona dret a l'assistència a classes així com tampoc compta com matrícula al centre.  Això implica no tenir seguiment ni suport per part del professorat més enllà del voluntari i totalment fora de la nostra jornada laboral.

Si teniu dubtes envieu un email al professorat voluntari, que us respondran tan aviat com puguin, però tingueu present que poden trigar varis dies en respondre i que depenent dels dubtes a vegades es fa molt difícil solucionar-ho via email.

És per aquest motiu que cal que sigueu el màxim d'autònoms possibles alhora de resoldre dubtes i fer les tasques amb temps i previsió.  Repasseu bé tots els materials i activitats prèvies fetes en les diferents assignatures i on encara teniu accés als Moodles corresponents.
## Entrega
L'entrega del treball constarà de la defensa del mateix davant d'un tribunal.  Caldrà fer-ne una presentació explicant com s'han fet tots els apartats tècnics i demostrant el seu funcionament.  Les dates es concretaran més endavant.
## Avaluació
Donada la natura de la compleció i el guiatge del projecte, aquest donarà peu a una **nota màxima de 7**.  Si es vol optar a **més nota cal afegir-hi apartats** com per exemple l'inclusiu d'un servei de correu electrònic, Alfresco, plans de contingència, afegir noves tecnologies no vistes a classe, o altres serveis no esmentats en aquesta guia.

A més, cal remarcar que la guia esmenta els punts clau que cal implementar, però més enllà d'aquests **es valorarà la qualitat del treball així com la funcionalitat plena** de tots els components.
# Bloc 1
## Situar-nos
- Repassar tota la documentació del Moodle del projecte de síntesi, especialment els documents d'exemple i ajudes.
## Compartir documentació
La idea és anar generant la documentació a mesura que s'avanci el projecte, de forma que en arribar a les dates d'entrega es pugui fer una correcció de la part nova generada.

Pe tant cal crear una carpeta al *Drive* del compte @lacetania.cat, compartir-l'ho amb permisos d'edició per a tothom que tingui l'enllaç i penjar l'enllaç a la tasca anomenada *"Treball de compleció"* que trobareu al Moodle de *MP12 Síntesi 24-25 (Matins)*.
# Bloc 2
## Introducció a l'empresa
Cal fer una introducció al treball explicant quin tipus d'empresa es vol construir, en el nostre cas caldrà explicar:
- Idea de negoci: Botiga d'informàtica de reparació i venda física i online.  També es vol captar empreses per a fer projectes puntuals i contractes de manteniment.
- Nom empresa: Us l'inventeu, però ha de ser únic.
- Logo empresa: Cal fer un logo que representi tant la idea de negoci com el nom triat.
- On estarà situada?
- A nivell de personal tindrem:
	- Cap
	- Encarregat de la botiga física: frontejarà, atendrà i en la mesura possible ajudarà a reparar.
	- Tècnic informàtic al taller: Estarà al taller reparant equips i mantindrà la xarxa de l'empresa.
	- 2x Tècnics informàtics d'empresa: O donaràn un cop de mà al tècnic del taller o faràn els projectes / manteniment a les empreses.
	- Encarregat de la botiga online: Prepararà comandes, gestionarà estoc, pagina i botiga web i farà de *community manager*.
	- Comercial: Itinerant i amb la missió de fer porta a porta a possibles empreses clients, fer detecció de necessitats i propostes de projectes.
## Introducció tècnica
Aquí cal lligar la idea d'empresa que s'ha exposat abans amb el que es farà a nivell tècnic.  Fes un cop d'ull als apartats i subapartats de la resta del treball per veure que caldrà que facis a nivell tècnic i intenta deduir i explicar com s'encaixaran en el dia a dia de l'empresa .  Explica-ho i justifica-ho.

*Per exemple, el DHCP està marcat que és per les dues Wifis i la subxarxa del taller.  Aquí hauriem d'explicar que tant els portàtils de treballadors i comercials, com els equips que entraran a ser reparats utilitzaran xarxes amb IP dinàmica per a no necessitar configuracions estàtiques, evitant així haver-ne de fer una gestió i control.*
## Plànol lògic
Cal omplir la següent taula amb les dades que creieu convenients i després plasmar tota aquesta informació a les etiquetes del plànol lògic de GNS3.  Cal remarcar que per ara el GNS3 tan sols és una eina visual, encara no cal que funcioni res.
### Xarxes i els seus rangs
| RANG           | XARXA        | FUNCIÓ                                   |
| -------------- | ------------ | ---------------------------------------- |
| xx.xx.xx.xx/xx | Internet     | Xarxa del host que dona Internet.        |
| xx.xx.xx.xx/xx | VLAN-DMZ     | Xarxa DMZ amb el servidor web.           |
| xx.xx.xx.xx/xx | VLAN-SRV     | Xarxa de servidors interns.              |
| xx.xx.xx.xx/xx | VLAN-INTERNA | Xarxa d'equips dels treballadors.        |
| xx.xx.xx.xx/xx | VLAN-TALLER  | Xarxa on connectar els equips a reparar. |
### IPs
Aquí especificarem les IPs dels equips amb IP fixa.

| IP                         | NOM_EQUIP           | FUNCIÓ                                                                  |
| -------------------------- | ------------------- | ----------------------------------------------------------------------- |
| xxx.xxx.xxx.xxx            | ROUTER INTERNET     | Interfície del router connectada a la xarxa del host que dona Internet. |
| xxx.xxx.xxx.xxx            | ROUTER VLAN-DMZ     | Interfície del router (gateway) connectada a la vlan DMZ.               |
| xxx.xxx.xxx.xxx            | ROUTER VLAN-SRV     | Interfície del router (gateway) connectada a la vlan SRV.               |
| xxx.xxx.xxx.xxx            | ROUTER VLAN-INTERNA | Interfície del router (gateway) connectada a la vlan INTERNA.           |
| xxx.xxx.xxx.xxx            | ROUTER VLAN-TALLER  | Interfície del router (gateway) connectada a la vlan TALLER.            |
| xxx.xxx.xxx.xxx            | SRV-AD              | Servidor del Active Directory                                           |
| xxx.xxx.xxx.xxx            | SRV-WEB             | Servidor Web.                                                           |
| xxx.xxx.xxx.xxx            | SRV-BACKUP          | Servidor de Backups.                                                    |
| xxx.xxx.xxx.xxx            | AP-TALLER           | Punt d'accés WiFi del taller.                                           |
| xxx.xxx.xxx.xxx            | PC-CAP              | PC del cap de l'empresa.                                                |
| xxx.xxx.xxx.xxx            | AP-INTERN           | Punt d'accés WiFi per treballadors.                                     |
| xxx.xxx.xxx.xxx            | TPV-BOTIGA          | TPV (PC) de la botiga física.                                           |
| xxx.xxx.xxx.xxx            | PC-TECNIC-1         | PC del tecnic de taller 1.                                              |
| xxx.xxx.xxx.xxx            | PC-TECNIC-2         | PC del tecnic de taller 2.                                              |
| xxx.xxx.xxx.xxx            | PC-TECNIC-3         | PC del tecnic de taller 3.                                              |
| xxx.xxx.xxx.xxx            | PC-ONLINE           | PC del gestor de la botiga online i community manager.                  |
| xxx.xxx.xxx.xxx-xxx (DHCP) | PORTATIL-COMERCIAL  | Portàtil del comercial.                                                 |
| xxx.xxx.xxx.xxx            | PRINTER             | Impressora en xarxa.                                                    |
| xxx.xxx.xxx.xxx-xxx (DHCP) | Equips Taller       | Els equips de clients que es connectin al taller aniran per DHCP.       |

### GNS3
Heu de reproduir la següent xarxa  a GNS3 i plasmar tota la informació tècnica de les taules anterior de forma que tan sols amb el plànol lògic ja es pugui saber tot.

![[Projectes/Mentor/Curs 25-26/gns3-complecio.png]]

## Plànol físic
Utilitzant el següent plànol de base, distribuïu els espais per usos i determineu on va cada element de xarxa del plànol lògic.  Un fet això, marqueu per on passaran les canaletes de cablejat de xarxa, marqueu les tomes de xarxa i assigneu-hi un codi que identifiqui el *patch pannel* i rosseta on van a parar en el rack.  Al *TALLER* afegiu vàries rossetes de xarxa, per a connectar-hi els PCs a reparar, encara que no hi hagin PCs.

També cal marcar on estarà el rack i per on entra la fibra òptica des del carrer fins arribar al rack.

Accediu al següent plànol i **feu-ne una còpia** a partir de la que treballar. Sobre la vostra còpia, heu de generar el plànol físic amb tots els elements esmentats
https://lucid.app/lucidchart/1198a799-ff11-489b-862b-6a27cf88feea/edit?invitationId=inv_35414304-1b8e-4f76-afdd-2a4313b40ffd
# Bloc 3
## Pressupostos
Cal que feu pressupostos de tots els elements informàtics necessaris per implementar el projecte, i que justifiqueu la tria.  Per tant cal escriure dues seccions a la memòria:
### Tria de components
Aquí cal mostrar els elements triats, destacant les seves característiques clau i justificant la tria, així com enllaçant la web del fabricant.
### Pressupostos
Cal generar pressupostos, agrupats per partides (xarxa, servidors, PCs, etc).  Cal que tinguin un format correcte de pressupost ([aquí un exemple](https://es.pinterest.com/pin/651403533635658127/)) i s'inclogui sobretot el P/N de cada element i l'IVA desglossat.
## SAI
Heu de fer els càlculs per a determinar quin SAI cal comprar per a mantenir un minim de 30 minuts els següents elements:
- SRV-WEB
- SRV-AD
- SWITCH-1
- ROUTER
- PC-CAP
Recordeu que el càlcul ha de ser amb VA i cal afegir un factor de correcció.

Un cop calculat, busqueu un SAI que compleixi els requisits i afegiu-ho als pressupostos.
# Bloc 4 (CORRECCIÓ)
Aquesta setmana es corregirà el bloc de tasques assignades des de l'inici del projecte fins el 21 de juliol.
## GNS3
Per ara farem l'enrutador amb una última versió de *Mikrotik CHR*, el switch amb un *Ethernet Switch* i el núvol amb un element *Cloud*.  La resta d'equips seran tots *VPCS* per ara i els anirem substituint per màquines virtuals a mesura que avancem en el projecte.
## Internet
Farem la configuració bàsica de xarxa, que inclourà el *router*, *switch* i *VPCS*.
### Switch
Configurarem el port que connecta amb el switch amb el tipus *dot1q* i un tag de *vlan* que no fem servir enlloc més, per exemple el 1.

La resta de ports els configurarem de tipus *access* i amb el tag de *vlan* que coincideixi amb el ran de la subxarxa assignada si es possible, sinó utilitzarem tags de desenes (10, 20 , 30, etc).
### Mikrotik
Caldrà configurar:
- VLANs, amb els mateixos tags que al switch i amb els noms que hem asignat al diagrama lògic.
- IPs de cada interfície i VLAN, seguint el que s'ha planificat al diagrama lògic.
- Source Nat pals paquets que surtin cap a la interfície d'Internet. Consulter punt 4.1 del [document d'ajuda de tallafocs](https://lacetanica.cat/apunts/SMX/MP12/Sintesi/SMX-MP12-Sintesi-Firewall_Mikrotik.html).
### VPCS
Per ara assignarem IPs seguint el que hem planificat al diagrama de xarxa lògic.
### Proves de connectivitat
Un cop arribat  aquest punt hauriem de poder fer ping des de qualsevol lloc a qualsevol lloc, inclòs Internet.  Feu proves des de cada subxarxa i cap a totes les subxarxes.
# Bloc 5
## AD
### Instal·lació AD
Substituïu el *VPCS* de *SRV-AD* per una màquina virtual de *VirtualBox*. Dimensioneu a nivell de recursos la *VM* de manera que pugueu fer anar el *AD *sense que el vostre *Host* quedi escanyat. Busqueu i instal·leu una de les últimes versions de *Active Directory*.  Assigneu a aquesta màquina **dues particions de disc** dimensionades de forma coherent, una la farem servir per instal·lar el sistema operatiu i l'altre per guardar les dades d'usuari.

Quan instal·leu recordeu triar el rols de servidors necessaris per al *AD* i sobretot **assignar el nom de la vostra empresa com a nom de domini** (*p.e.: gimenez.cat*).
### Usuaris i grups
Creeu els grups seguint les pautes del plantejament l'empresa (cada perfil ha de ser un grup).  Addicionalment crearem el grups següents:
- COPIES: Per als responsables de les còpies de seguretat.
- XARXA: Per als responsables de gestionar la xarxa.
- PUBLICADOR: Per aquells usuaris que podran editar documents que finalment seran públics.
Crea usuaris amb noms aleatoris i assigna'ls a cadascun dels rols que hem definit inicialment al plantejament de l'empresa.   Addicionalment assigna el rol de COPIES a un tècnic, el de XARXES a un altre tècnics i PUBLICADOR al que s'encarrega de la botiga online i també al comercial.  Finalment el CAP ha d'estar a tots els grups.
## Clients
Cal substituir *PC-CAP*, * PC-TECNIC-1* i *PC-REPARAR* per clients Windows Pro (últimes versions) i fer que els dos primers pengin del *Domini*.
# Bloc 6
## Carpetes compartides
A disc dur secundari del *SRV-AD* crearem una estructura de carpetes compartides.
- Direcció: Tan sols accés el Cap.
- Reparacions: Accés total els tècnics, lectura el botiga física.
- Vendes: Accés total per al comercial, encarregat botiga física i botiga online. Lectura per als tècnics.
- Interna: Accés de lectura per tothom, d'escriptura tan sols cap i el tècnic de taller.
- Impressions: Aquí aniràn a parar les impressions en PDF, per tant tothom ha de tenir permissos per llegir i escriure.  Tanmateix restringiu el permís d'eliminar al Cap i Tècnic de Taller.
El *Cap* ha de tenir accés total a totes les carpetes.

Cal crear un accés directe al directori compartit general a l'escriptori de *PC-CAP* i *PC-TECNIC-1*.
# Bloc 7
## Perfils
Cal afegir la funcionalitat de perfils mòbils per a tots els usuaris.  Les carpetes de perfils han d'estar desades al disc dur secundari del *SRV-AD*.
## Política de contrasenyes
### Implementació tècnica
Al *SRV-AD* cal implementar la política de contrasenyes per a tot el domini on:
- Contrasenyes siguin robustes.
- Caduquin cada any.
- Historial de contrasenyes de 3.
- Vigència mínima de 1 mes.
- El compte es bloquegi 5 minuts en fallar 3 intents.
### Procediments
Recordar que el Tècnic de Taller, junt amb el Cap, és qui ha de gestionar la xarxa de l'empresa, inclòs el *SRV-AD*, i per tant és l'únic que pot gestionar les contrasenyes.

Per tant redacteu la part de procediment de la política de contrasenyes seguint aquestes idees.
## GPOs
Implementeu una GPOs que faci que el fons de pantalla de tots els equips del domini sigui un fons de color blau amb el logo de l'empresa gran i centrat.
## Impressora compartida
Finalment creeu una impressora compartida amb tot el personal de l'empresa al *SRV-AD* que permeti imprimir en PDFs i deixi les impressions a la carpeta compartida de *IMPRESSIONS*.
# Bloc 8 (CORRECCIÓ)
Cal tenir entregat tots els apartats des de l'última correcció fins a avui (GNS3->Impressora compartida).
## DNS
Al DNS cal fer una entrada per a cada equip i servidor de la xarxa. Important que el *SRV-WEB* es digui *www*.
Asdicionalment cal crear els següents alias:
- moodle: Per al *SRV-WEB*.
- botiga: Per al *SRV-WEB*.
- compartida: Per al *SRV-AD*.
- printer: Per a l'impressora.
## DHCP
En el diagrama *GNS3* farem que els dos *AP* siguin *VPCS* amb *DHCP*, i els utilitzarem com a referència per verificar que el DHCP funciona correctament.

Cal configurar el *Router Mikrotik* per a que doni DHCP per les interfícies *VLAN-TALLER* i *VLAN-INTERNA*, cadascuna d'elles amb el rang pertinent de IPs.

Caldrà fer una reserva de IPs en e#l DHCP corresponent a *VLAN-INTERNA* per a respectar les IPs dels PCs que apareixen en el digrama de xarxa, així del *AP*.  Passeu tots els equips d'aquesta VLAN a DHCP i verifiqueu que reben les IPs que els hi pertoquen.

En la *VLAN-TALLER* no cal fer reserva i també tots els equips d'aquest VLAN han d'anar per DHCP.
# Bloc 9
## Servidor web
Substituïm el VPCS *SRV-WEB* per una màquina virtual amb Debian (última versió).  Aquí cal instal·lar un LAMP.  També instal·leu certificat digital per a funcionar per *HTTPS*.

Un cop fet, i per a fer proves, creeu tres carpetes a */var/www/html* i un *index.html* personalitzat que us servirà per fer verificacions i proves de bon funcionament:
- principal: Amb un index.html que contingui el text "principal".
- moodle: Amb un index.html que contingui el text "moodle".
- botiga: Amb un index.html que contingui el text "botiga".
Un cop creada aquesta estructura cal que configureu tres *virtualhosts*, un per a cadascun d'ells, lligats als dominis següents:
- www.domini.cat: Ha d'apuntar cap a principal.
- moodle.domini.cat: Ha d'apuntar cap al moodle.
- botiga.domini.cat: Ha d'apuntar cap a la botgia.
És **molt important** que feu també que tota connexió *HTTP* es redirigeixi de forma automàtica a *HTTPS*.
## Accés remot
Instal·leu també al *SRV-WEB* el servidor *OPENSSH-SERVER* per accedir-hi de forma remota.  Feu que l'accés es pugui fer utilitzant certificats digitals per identificar l'usuari client (que no calgui password per accedir-hi, sinó que vagi amb certificats digitals).
# Bloc 10
## HTML+CSS
Crea una *landing page* amb HTML i CSS que contingui els apartats següents:
- Introducció a l'empresa (que fem, etc).
- Serveis que oferim.
- Quin és el nostre equip de persones.
- Opinions de clients.
- Contacte.
- Enllaços a la botiga (wordpress) i moodle.
La pàgina ha de ser atractiva visualment i seguir una estètica homogènia amb el proper *wordpress* que implementarà la botiga.

A més, cal que:
- L'estructura principal estigui feta amb *Grid Box*, i canvii quan la pàgina es visualitzi en un mòbil (és a dir, la web ha de ser *responsive* i **modificar la seva estructura** entre pantalles grans i petites).
- Hi ha d'haver una serie de caixes (per exemple en presentar l'equip de persones) que ha d'estar feta en un *Flex Box* de forma que les caixes es redistribueixin depenent de la mida de la pantalla.
- Cal seguir les indicacions donades a M8 respecte a un codi ben fet.
Remarcar que en aquest apartat cal demostrar que s'hi han dedicat hores, tot aprofundint en aspectes tècnics i personalitzacions.
# Bloc 11
## Wordpress
Cal instal·lar el *wordpress* a la carpeta corresponent del *SRV-WEB* de manera que hi accedim per https://botiga.domini.cat/.

S'ha de modificar el tema de *wordpress* per a que segueixi l'estètica marcada per la *landing page*.  També personalitzar el *wordpress* en el seu conjunt.

S'han de crear varis usuaris, un pel tècnic i un altre pel cap que tindràn permisos totals i un altre per a la persona encarregada de la botiga virtual que tindrà permisos d'edició.

S'ha d'afegir un *plugin* per a *e-commerce* que converteixi el *wordpress* en una botiga virtual.  Allà hi configurarem varis productes, amb totes les seves característiques i la vestirem correctament.  Cal cuidar que la botiga virtual es vegi complerta, i s'hi pugui fer tot el procés (en la mesura del possible) de compra.

De nou remarcar que en aquest apartat cal demostrar que s'hi han dedicat hores, tot aprofundint en configuracions i personalitzacions.
# Bloc 12 (CORRECCIÓ)
Cal tenir entregat i documentat des de DNS fins Wordpress.
##  Moodle
Cal instal·lar el *moodle* a la carpeta corresponent del *SRV-WEB* de manera que hi accedim per https://moodle.domini.cat/.

S'ha de modificar el tema per a que segueixi l'estètica marcada per la *landing page*.  També cal personalitzar el *moodle* en el seu conjunt.

De nou, el tècnic i el cap tindran permisos totals i la resta d'usuaris necessitaran un perfil d'estudiant.

Cal crear 4 cursos de temàtiques relacionades amb l'empresa (p.e.: Curs bàsic de reparació d'equips, Curs de gestió de Wordpress, Curs de E-Commerc i SEO, Curs de Community Manager, etc).  Un d'ells cal treballar-l'ho de forma que contingui:
- El curs ha de ser temàticament complert.
- Ha de contenir materials escrits i un vídeo tutorial.
- Ha de contenir activitats de com a mínim 4 tipus diferents, totes elles ben configurades i treballades.
- Ha de tenir usuaris assignats i s'ha de permetre l'accés a visitants.
De nou remarcar que en aquest apartat cal demostrar que s'hi han dedicat hores, tot aprofundint en configuracions i personalitzacions.
# Bloc 13
## Còpies de seguretat
Substituirem el *SRV-BACKUP* per una màquina virtual amb Debian (última versió).

Cal aconseguir fer aquest esquema de còpies del *SRV-WEB*:
- 1 Complerta mensual (dia 1).
- 1 Diferencial mensual (dia 15).
- 1 Incremental diària.
Totes a les 01:00AM i que incloguin:
- Bases de dades.
- Arxius web de Moodle, Wordpress i Landing Page.
- Arxius de configuració del *SRV-WEB*.

Aquestes còpies s'han de fer amb *TAR* i el *SRV-BACKUP* les ha de recuperar a les 03:00AM del *SRV-WEB* mitjançant *scp*.

En definitiva s'ha de fer un sistema de còpies igual al fet al treball de MP06-UF2.  Consulteu l'enunciat dins del seu Moodle per més informació.

Teniu material de referència aquí:
- https://lacetanica.cat/apunts//SMX/MP06/UF2/SMX-MP06-UF2-T_CopiesSeguretat.html
# Bloc 14
## Tallafocs

Teniu material de referència aquí:
- https://lacetanica.cat/apunts/SMX/MP12/Sintesi/SMX-MP12-Sintesi-Firewall_Mikrotik.html
- https://lacetanica.cat/apunts/SMX/MP06/UF5/SMX-MP06-UF5-mikrotikLlistesBlanques.html
Cal configurar un tallafocs de llistes blanques al *router Mikrotik*.  Les connexions permeses han de ser:
- Tots els equips han de poder fer ping a tot arreu.
- De la *VLAN-INTERNA* s'ha de poder fer login al domini, accedir a les carpetes compartides i imprimir.
- Totes les VLAN excepte la DMZ han de poder navegar per Internet.
- La *VLAN-INTERNA* ha de poder accedir a la web de la DMZ i per SSH al servidor de la DMZ.
- Des de Internet s'ha de poder accedir a les webs de la DMZ.
- Cal redirigir les connexions web entrants des de Internet cap al servidor web DMZ.
- Cal permetre al *SRV-BACKUP* accedir per *ssh* al *SRV-WEB*.
Qualsevol altre connexió no ha d'estar permesa.  Cal remarcar que si afegiu serveis més enllà d'aquesta guia caldrà modificar el tallafocs en conseqüència.
# Bloc 15
## Programació
Cal crear un programa amb *Python* que guardi informació sobre l'estoc de material a magatzem.  Les funcionalitats que ha de tenir són:
- Guardar l'estoc actual en un arxiu de text que faci les funcions de base de dades.
- Permetre afegir nous articles a l'estoc.
- Permetre eliminar totalment un article.
- Permetre sumar quantitats a l'estoc d'un article determinat.
- Permetre restar quantitats a l'estoc d'un article determinat.
- Permetre llistar tot l'estoc.
- Permetre llistat els articles amb estoc 0.
- Permetre llistat els articles amb menys de estoc X, on X es demanarà de forma interactiva a l'usuari.
Aquest programa es valorarà la funcionalitat com sobretot el bon ús del codi i funcions.  Seguiu les pautes vistes a programació.
# Bloc 16 (CORRECCIÓ)
Cal tenir entregat des de Moodle fins al final de treball, junt amb tots els apartats extres que volgueu afegir.  Aquesta serà l'última correcció.
## Documentació
Cal rematar la documentació, verificant sobretot estructura, estil i faltes.  Quan estigui finalitzada, i abans de la data màxima d'entrega, cal exportar-la a PDF i deixar-l'ho a la carpeta compartida del projecte.
## Presentació
Crear una presentació amb l'eina que trieu per a fer la defensa del projecte.  En aquesta defensa caldrà fer una breu introducció a l'empresa des del punt de vista de donar-se a conèixer i a partir d'aquí explicar els aspectes tècnics de la seva implementació preferiblement fent demostracions de com s'han configurat el elements i demostrant el seu bon funcionament.

Aquesta presentació ha de durar aproximadament 30 minuts, després farem 15 minuts de preguntes i finalment el tribunal debatrà la nota durant 15 minuts més.

# Bloc 17
Entrega final fent la defensa del projecte davant un petit tribunal.