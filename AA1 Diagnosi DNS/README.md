## Enunciat de l'activitat

### Activitat: Projecte de Consultoria DNS – TechCloud Solutions

#### 1. Context de l'activitat
Com a tècnics en pràctiques de l'empresa de consultoria i serveis IT TechCloud Solutions, se us ha assignat el primer projecte per a un client real: Innovació Tecnològica del Maresme S.L.

El client experimenta incidents de connectivitat, lentitud en la resolució de dominis i dubtes sobre la configuració dels seus servidors de noms. El projecte consta de dues fases:

- **Formació tècnica al client:** Disseny d'un recurs educatiu per explicar el funcionament del protocol DNS a nivell teòric.
- **Diagnosi i auditoria de la xarxa:** Execució d'una auditoria amb eines de línia de comandes (CLI) en un entorn controlat per analitzar registres, temps de resposta i resolució local.

#### 2. Fase Teòrica: Píndola formativa i mapa conceptual
Heu de preparar un mapa conceptual i enregistrar un recurs audiovisual per al personal tècnic del client que cobreixi els punts següents:

- **Concepte de DNS:** Definició, objectius principals i exemples gràfics d'aplicació.
- **Gestió de dominis:** Procés de contractació i registre d'un nom de domini.
- **Arquitectura DNS:** Elements principals i serveis que intervenen en el sistema.
- **Estructura jeràrquica:** Organització en arbre del sistema de noms.
- **Procés de resolució:** Funcionament de les consultes iteratives vs. recursives, i el rol dels Root Servers i servidors autoritatius.
- **Tipus de zones:** Zona directa vs. zona inversa; zona primària vs. zona secundària.
- **Resolució local:** Funcionament de la resolució de noms sense servidor centralitzat en xarxa local (protocol mDNS).

**Entregable de la fase teòrica:** Enregistreu una píndola formativa en vídeo (individual) d'entre 5 i 10 minuts de durada on s'expliquin de manera clara, breu i visual tots els conceptes anteriors recolzant-vos en el mapa conceptual.

#### 3. Fase Pràctica: Auditoria de resolució de noms (CLI)

**Requisits de l'entorn de treball**
- Sistema operatiu: Màquina virtual amb Zorin OS (o distribució Linux equivalent).
- Configuració de xarxa:
  - Interfície 1 (`eth0` / `enp0s3`): Mode NAT (amb sortida a Internet).
  - Interfície 2 (`eth1` / `enp0s8`): Mode Adaptador pont (Bridged) amb IP estàtica i paràmetres assignats pel responsable tècnic.

**Part A. Diagnosi avançada amb `dig` (Linux/macOS)**
Executeu les comandes següents des de la terminal i incloeu-ne l'anàlisi corresponent utilitzant el domini `tecnocampus.cat`:

1. Consulta bàsica de registre A: `dig tecnocampus.cat A`
   - Anàlisi: Identifiqueu la IP de resposta, el valor del TTL i la IP del servidor DNS que ha respost.
2. Consulta de servidors de noms (NS): `dig tecnocampus.cat NS`
   - Anàlisi: Indiqueu quins són els servidors de noms (Name Servers) autoritatius per a aquest domini.
3. Consulta detallada SOA: `dig tecnocampus.cat SOA`
   - Anàlisi: Identifiqueu el correu de l'administrador (`rname`) i el número de sèrie (`serial`) del domini.
4. Consulta de resolució inversa: `dig -x <IP_obtinguda_a_la_comanda_1>`
   - Anàlisi: Detalleu quina informació s'obté dels registres `PTR` i a quin nom de domini resol la IP introduïda.

**Part B. Comprovació de resolució amb `nslookup` (Mode interactiu)**
Obriu l'eina `nslookup` en mode interactiu executant `nslookup` a la terminal fins a veure el prompt (`>`).

Instruccions de control: `set type=TIPUS` (defineix el registre: A, NS, SOA, etc.), `server IP_o_NOM` (canvia el servidor de consulta), `exit` (surt del prompt).

5. Consulta bàsica no autoritativa: dins del prompt, executeu `set type=A` i `tecnocampus.cat`
   - Anàlisi: Analitzeu la resposta obtinguda i indiqueu per què la consola especifica que la resposta és no autoritativa (Non-authoritative answer).
6. Consulta autoritativa directa: canvieu el servidor DNS pel primer servidor autoritatiu obtingut a la Comanda 2 i executeu novament la consulta del registre A per a `tecnocampus.cat`.
   - Anàlisi: Compareu la resposta amb la de la Comanda 5 i confirmeu si l'indicador "no autoritatiu" ha desaparegut.

**Part C. Resolucions locals i protocol mDNS**
Comproveu la resolució local entre equips de la mateixa xarxa sense servidor DNS dedicat:

1. Verifiqueu el nom d'host de la vostra màquina Zorin OS amb la comanda `hostname`.
2. Des d'un altre equip de la mateixa xarxa local (o xarxa bridged), executeu: `ping <hostname>.local`
3. Anàlisi: Descriviu el funcionament del protocol mDNS (Multicast DNS), quin port utilitza (UDP 5353) i quin avantatge aporta en entorns sense servidor DNS configurat.

#### 4. Instruccions de lliurament
Pugeu a la tasca de Moodle un fitxer comprimit en format `.zip` amb la nomenclatura `Cognoms_Nom_Practica_DNS_Comandes.zip`. El fitxer ha de contenir el document `guia.md` amb:
- Enllaç al vídeo de la píndola formativa (YouTube, Vimeo o Google Drive amb permisos de visualització oberts).
- Captures de pantalla clares de l'execució de les 6 comandes (`dig` i `nslookup`) i de les proves de mDNS.
- Respostes analítiques i justificacions tècniques a cadascun dels punts demanats.
- Comprovació de la configuració de les dues interfícies de xarxa (`ip a` o `ifconfig`).
- Apartat de fonts i eines consultades (declaració de l'ús d'eines d'IA generativa o enllaços a la documentació utilitzada).

---
