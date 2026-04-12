# Projet GRE over IPsec VPN - Simulation GNS3

## 📋 Présentation du projet

Ce laboratoire illustre la mise en place d'un **tunnel GRE chiffré par IPsec** entre deux sites distants connectés via un fournisseur d'accès Internet (ISP), simulé avec **GNS3**.

Le tunnel chiffre le trafic GRE à l'aide d'IPsec (IKEv1 + ESP-AES + SHA-HMAC), permettant aux deux réseaux locaux de communiquer de façon sécurisée sur Internet.

---

## 🗺️ Topologie réseau

<img width="500" height="473" alt="1" src="https://github.com/user-attachments/assets/7a241593-9cc8-422e-b8fd-67234233172f" />

---

## 📦 Tableau d'adressage IP

| Équipement | Interface       | Adresse IP          | Masque          | Description         |
|------------|-----------------|---------------------|-----------------|---------------------|
| ISP        | Serial0/0       | 33.33.33.1          | 255.255.255.252 | Lien vers R1        |
| ISP        | Serial0/1       | 44.44.44.1          | 255.255.255.252 | Lien vers R2        |
| R1         | Serial5/0       | 33.33.33.2          | 255.255.255.252 | Lien vers ISP       |
| R1         | FastEthernet0/0 | 192.168.12.1        | 255.255.255.0   | Lien vers le LAN 1  |
| R1         | Tunnel0         | 172.16.0.1          | 255.255.255.252 | Tunnel GRE          |
| R2         | Serial5/0       | 44.44.44.2          | 255.255.255.252 | Lien vers ISP       |
| R2         | FastEthernet0/0 | 192.168.100.1       | 255.255.255.0   | Lien vers le LAN 2  |
| R2         | Tunnel0         | 172.16.0.2          | 255.255.255.252 | Tunnel GRE          |
| PC1        | e0              | DHCP (192.168.12.x) | 255.255.255.0   | Client LAN 1        |
| PC2        | e0              | DHCP (192.168.100.x)| 255.255.255.0   | Client LAN 2        |

---

## 🔐 Résumé de la configuration VPN

| Paramètre         | Valeur                              |
|-------------------|-------------------------------------|
| Type de VPN       | GRE over IPsec                      |
| Politique IKE     | AES, SHA, Groupe 2                  |
| Clé pré-partagée  | cisco                               |
| Transform Set     | ESP-AES + ESP-SHA-HMAC              |
| Mode              | Transport                           |
| ACL               | Autoriser GRE entre les IPs publics |

---

## ⚙️ Technologies utilisées

- **GNS3** — Environnement de simulation réseau
- **Cisco IOS** — Système d'exploitation des routeurs
- **GRE Tunnel** — Protocole de tunneling de couche 3
- **IPsec IKEv1** — Échange de clés et chiffrement
- **ESP-AES + ESP-SHA-HMAC** — Chiffrement et intégrité des données
- **Routage statique** — Accessibilité du tunnel et des LANs
- **DHCP** — Attribution automatique des adresses IP
- **Wireshark** — Analyse du trafic réseau

---

## 📊 Résultats attendus

- État ISAKMP SA : **QM_IDLE (ACTIVE)**
- IPsec SA : les compteurs de chiffrement/déchiffrement s'incrémentent
- PC1 peut **pinguer** PC2 et vice versa avec succès
- Wireshark : le trafic apparaît en **ESP** chiffré entre 33.33.33.2 ↔ 44.44.44.2

---

## ✅  vérification
- R1
  
<img width="375" height="153" alt="1" src="https://github.com/user-attachments/assets/4c0bf01b-b557-4009-b66a-0219aa415700" />
<img width="436" height="110" alt="3" src="https://github.com/user-attachments/assets/c3c4c4a1-eb25-4ab0-a259-b1ca636a5be0" />
<img width="500" height="348" alt="4" src="https://github.com/user-attachments/assets/ada7bb4b-5b18-4a65-9329-3f3aa13cc598" />

---
- R2
<img width="371" height="152" alt="1" src="https://github.com/user-attachments/assets/c73b2e9e-ec38-400c-9a0d-c3995524720a" />
<img width="426" height="110" alt="3" src="https://github.com/user-attachments/assets/1d2f010d-c59a-4cff-862b-373f7a7b2788" />
<img width="500" height="348" alt="4" src="https://github.com/user-attachments/assets/60d0fc9e-4b20-44dc-b413-d018b60df1af" />



---
### Connectivity Testing & DHCP Validation
 Tests de connectivité réussis entre les deux sites. Les machines clientes (PC1 et PC2) reçoivent leurs adresses IP via DHCP et peuvent communiquer à travers le  tunnel VPN. Le premier Ping montre un léger délai (Timeout) dû à l'initialisation de la négociation IKE (Phase 1 & 2), suivi d'une latence stable.

- PC1
  
 <img width="475" height="283" alt="pc1" src="https://github.com/user-attachments/assets/9c876564-69bb-4f12-8207-d9b9fe7b3336" />

- PC2
  
 <img width="445" height="166" alt="pc2" src="https://github.com/user-attachments/assets/506d7e76-b04a-4a90-b913-a4af234d3d76" />

---
### Traffic Encryption Analysis (Wireshark)
 Capture Wireshark montrant le flux de données entre les adresses publiques (33.33.33.2 et 44.44.44.2). On observe l'utilisation du protocole ESP, ce qui        confirme que le tunnel IPsec encapsule et chiffre tout le trafic (ICMP, Routage, etc.). Le contenu original des paquets est invisible pour l'ISP.

  <img width="1273" height="501" alt="4" src="https://github.com/user-attachments/assets/462a58b8-086e-4ea0-93d4-c112d7e435f6" />

---

## 👨‍💻 Auteur

**Mohamed ECH-chafiy**
- Étudiant en Infrastructure Digitale — Option Systèmes & Réseaux  
- OFPPT, Arrahma, Casablanca, Maroc  
- Linkedin : www.linkedin.com/in/mohamed-ech-chafiy

---
