# Projecte de Consultoria DNS – TechCloud Solutions

**Client:** Innovació Tecnològica del Maresme S.L.
**Tècnic:** Jordi Evstegneev
**Mòdul:** 0227 Serveis de xarxa – CFGM SMX
**Data:** 05/11/2026

---

## 1. Vídeo explicatiu del DNS

- **Enllaç al vídeo:** [ENGANXA AQUÍ L'ENLLAÇ DE YOUTUBE]
- **Durada:** 6:09

---

## 2. Entorn de treball i configuració de xarxa

**Sistema operatiu:** Zorin OS (basat en Ubuntu 24.04) a VirtualBox
**Nom de la màquina:** `usuari-VirtualBox`

Comanda utilitzada: `ip a`

![Configuració interfícies](img/00_ip_a.png)

| Interfície | Mode VirtualBox | IP | MAC | Funció |
|---|---|---|---|---|
| lo | – | 127.0.0.1/8 | – | Loopback (el propi equip) |
| enp0s3 | NAT | 10.0.2.6/24 | 08:00:27:45:64:24 | Sortida a Internet a través de l'amfitrió |
| enp0s8 | Adaptador pont (Bridged) | 192.168.1.200/24 (estàtica) | 08:00:27:d2:fa:b6 | Connexió directa a la xarxa local |

Paràmetres estàtics de `enp0s8`: IP 192.168.1.200 · màscara 255.255.255.0 · porta d'enllaç 192.168.1.1 · DNS 8.8.8.8

**Comentari:**
- `enp0s3` està en mode **NAT** i rep la IP per DHCP de VirtualBox (per això apareix `dynamic`). És la que dona accés a Internet per fer les consultes DNS.
- `enp0s8` està en mode **adaptador pont** amb **IP estàtica**: ja no apareix la paraula `dynamic` i el temps de vida és `forever`. Aquesta interfície connecta la màquina directament a la xarxa local, com si fos un equip més, i això permet que altres equips la trobin (prova de mDNS).
- Les dues interfícies estan en estat `UP`.

---

## 3. Part A – Diagnosi amb `dig`

### Comanda 1 – Registre A

```bash
dig tecnocampus.cat A
```

![dig A](img/01_dig_A.png)

**Anàlisi:**

- **Estat:** `NOERROR` → la consulta s'ha resolt correctament.
- **IPs de resposta (ANSWER SECTION):** el domini té 4 registres A:
  - 18.172.213.97
  - 18.172.213.8
  - 18.172.213.22
  - 18.172.213.110

  Tenir diverses IPs serveix per repartir la càrrega i tenir redundància (el web està allotjat a Amazon CloudFront).
- **TTL:** **60 segons**. És el temps que la resposta es pot guardar a la cache abans de tornar a preguntar. És un TTL molt baix, típic de serveis al núvol que poden canviar d'IP sovint.
- **Servidor DNS que ha respost:** `127.0.0.53#53` (port 53, UDP). És el resolver local de Linux (*systemd-resolved*), que reenvia la consulta al DNS de la xarxa i guarda les respostes a la cache.
- **Flags:** `qr rd ra` → és una resposta (`qr`), s'ha demanat recursivitat (`rd`) i el servidor la permet (`ra`). **No apareix `aa`**, per tant la resposta **no és autoritativa**.
- **Query time:** 22 ms.

### Comanda 2 – Servidors de noms (NS)

```bash
dig tecnocampus.cat NS
```

![dig NS](img/02_dig_NS.png)

**Anàlisi:**
