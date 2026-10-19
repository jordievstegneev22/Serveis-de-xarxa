<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=blur&color=0:1E3C72,100:2A5298&height=200&section=header&text=Serveis%20de%20Xarxa&fontSize=52&fontColor=ffffff&desc=MP%200227%20-%202n%20SMX&descSize=18&descAlignY=70&animation=twinkling"/>
</p>

<p align="center">
  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&duration=3000&pause=800&color=36BCF7&center=true&vCenter=true&width=500&lines=Configuraci%C3%B3+de+serveis+en+Linux;Ubuntu+Server+%2B+Zorin+OS;DHCP+amb+Kea;An%C3%A0lisi+amb+Wireshark"/>
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Ubuntu_Server-24.04_LTS-E95420?style=for-the-badge&logo=ubuntu&logoColor=white">
  <img src="https://img.shields.io/badge/Zorin_OS-Client-15A6F0?style=for-the-badge&logo=linux&logoColor=white">
  <img src="https://img.shields.io/badge/VirtualBox-VM-183A61?style=for-the-badge&logo=virtualbox&logoColor=white">
  <img src="https://img.shields.io/badge/Kea-DHCP-0A9EDC?style=for-the-badge&logo=isc&logoColor=white">
  <img src="https://img.shields.io/badge/Wireshark-An%C3%A0lisi-1679A7?style=for-the-badge&logo=wireshark&logoColor=white">
</p>

<p align="center">
  <img src="https://img.shields.io/github/last-commit/jordievstegneev22/Serveis-de-xarxa?style=flat-square&color=blue">
  <img src="https://img.shields.io/github/repo-size/jordievstegneev22/Serveis-de-xarxa?style=flat-square&color=green">
  <img src="https://img.shields.io/github/commit-activity/m/jordievstegneev22/Serveis-de-xarxa?style=flat-square&color=orange">
</p>

<img src="https://capsule-render.vercel.app/api?type=rect&color=0:1E3C72,100:2A5298&height=3"/>

## 📂 Contingut

| | Activitat | Descripció | Estat |
| :--: | --- | --- | :--: |
| 🖧 | [**AA2 · Avaluació Server DHCP**](./AA2-Avaluaci-Server-DHCP.d.d.d.d) | Desplegament i configuració d'un servidor DHCP amb Kea, comprovació des del client i anàlisi del procés DORA. | ✅ |
| 🔜 | *Properes activitats* | El repositori s'anirà ampliant durant el curs. | ⏳ |

<img src="https://capsule-render.vercel.app/api?type=rect&color=0:1E3C72,100:2A5298&height=3"/>

## 🔄 El procés DORA

```mermaid
sequenceDiagram
    participant C as 💻 Client (Zorin OS)
    participant S as 🖥️ Servidor (Kea DHCP)
    C->>S: 1. DISCOVER (broadcast)
    S->>C: 2. OFFER (adreça disponible)
    C->>S: 3. REQUEST (accepta l'oferta)
    S->>C: 4. ACK (concessió confirmada)
```

<details>
<summary>🛠️ <b>Entorn de treball</b> (clica per desplegar)</summary>

<br>

| Component | Eina |
| --- | --- |
| 🖥️ Servidor | Ubuntu Server 24.04 LTS |
| 💻 Client | Zorin OS Core |
| 📦 Virtualització | VirtualBox |
| 🌍 Serveis | Kea DHCP · Netplan · SSH |
| 🔍 Anàlisi | Wireshark |

</details>

<details>
<summary>📋 <b>Com està organitzat</b></summary>

<br>

Cada activitat té la seva carpeta amb el document de lliurament i les captures
que serveixen d'evidència. En les pràctiques es documenta el **valor esperat**,
el **valor observat** i la **conclusió** de cada comprovació.

</details>

> [!NOTE]
> Repositori acadèmic del cicle de Sistemes Microinformàtics i Xarxes (SMX).

<p align="center">
  <sub>👤 <b>Jordi Evstegneev</b> · 2n SMX · Curs 2025–2026</sub>
</p>

<img src="https://capsule-render.vercel.app/api?type=blur&color=0:2A5298,100:1E3C72&height=140&section=footer"/>