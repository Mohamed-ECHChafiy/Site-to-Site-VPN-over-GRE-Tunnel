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

