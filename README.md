# Site to Site VPN over GRE Tunnel

## Architecture du Réseau
Ce projet présente la mise en œuvre d'une architecture réseau sécurisée reliant deux sites distants (R1 et R2) à travers un réseau public (ISP). L'objectif est de permettre une communication fluide et sécurisée entre les réseaux locaux (LAN) en utilisant un tunnel GRE encapsulé dans un profil IPsec.

## Technologies Utilisées

#### *GRE (Generic Routing Encapsulation) : Pour permettre le passage des protocoles de routage .
#### *IPsec (Internet Protocol Security) : Pour le chiffrement (Encryption) et l'intégrité.
#### *Crypto Maps / Virtual Tunnel Interface (VTI).
#### *GNS3 : Pour la simulation.

## Aperçu du Lab
<img width="593" height="473" alt="1" src="https://github.com/user-attachments/assets/0fe9eba7-cc5e-486b-b52f-ec85c7ff2c88" />

## Config ISP
 <img width="349" height="153" alt="2" src="https://github.com/user-attachments/assets/2141d4dc-fb14-44fd-b7d4-bccab4f07692" />
 <img width="633" height="90" alt="1" src="https://github.com/user-attachments/assets/f540a87d-a8d6-48d6-9593-a7d70b39ba83" />

## Config R1

<img width="348" height="292" alt="6" src="https://github.com/user-attachments/assets/a654d86a-0a9f-4332-bc05-9bd4542806f1" />
<img width="374" height="238" alt="10" src="https://github.com/user-attachments/assets/98e121e2-b6ed-43c5-9767-444e78310f73" />
<img width="436" height="110" alt="3" src="https://github.com/user-attachments/assets/4f7bb42d-32eb-46db-a88b-781fdd703e0c" />
<img width="542" height="348" alt="4" src="https://github.com/user-attachments/assets/38021f6b-d929-428e-840f-80527758a99b" />

## Config R2

<img width="336" height="257" alt="6" src="https://github.com/user-attachments/assets/5f33e4db-dcfd-4af3-a28b-42c46e2eedfb" />
<img width="412" height="241" alt="10" src="https://github.com/user-attachments/assets/c2ef610a-91fe-4f85-a287-08a242b95b0c" />
<img width="426" height="110" alt="3" src="https://github.com/user-attachments/assets/90bfe7ed-f40f-4399-b84f-c470df19e9e6" />
<img width="541" height="348" alt="4" src="https://github.com/user-attachments/assets/2ed71f6d-76b9-4014-b832-b7d0105efad1" />

## Connectivity Testing & DHCP Validation
### Tests de connectivité réussis entre les deux sites. Les machines clientes (PC1 et PC2) reçoivent leurs adresses IP via DHCP et peuvent communiquer à travers le tunnel VPN. Le premier Ping montre un léger délai (Timeout) dû à l'initialisation de la négociation IKE (Phase 1 & 2), suivi d'une latence stable.
### PC1
<img width="475" height="283" alt="pc1" src="https://github.com/user-attachments/assets/acd3061e-5d3d-4895-81e1-579b861d8c67" />

### PC2
<img width="445" height="166" alt="pc2" src="https://github.com/user-attachments/assets/61b387e7-a8f4-45b0-b114-53fe92d0a6f4" />

## Traffic Encryption Analysis (Wireshark)
#### Capture Wireshark montrant le flux de données entre les adresses publiques (33.33.33.2 et 44.44.44.2). On observe l'utilisation du protocole ESP, ce qui confirme que le tunnel IPsec encapsule et chiffre tout le trafic (ICMP, Routage, etc.). Le contenu original des paquets est invisible pour l'ISP.

<img width="1273" height="501" alt="4" src="https://github.com/user-attachments/assets/dad3c55b-6af8-46db-96da-7d29cc5b8e2a" />
