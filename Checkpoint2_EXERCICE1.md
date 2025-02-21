# CHECKPOINT2
## a) SERVICES DE CONEXTION
La machine serveur et la machine client ne communique pas 
## b) comunication entre deux machine
Les ping ne marche pas , parce que il sont pas dans le meme reseau
Machine SERVEUR @IP 172.16.10.10 /24
Machine CLIENTE @IP 172.16.100.50/24 
ET je change le adress IP de client par 172.16.10.20/24 
<img width="200" alt="image" src="https://github.com/user-attachments/assets/a479443e-7306-4632-a2ca-65166e683264" />
### 1.1 pig avec la machine serveur 
<img width="328" alt="image" src="https://github.com/user-attachments/assets/bf1edaa0-00da-4732-8513-1153ac2e65c6" />

#### ping avec la machine client
<img width="260" alt="image" src="https://github.com/user-attachments/assets/16012066-e340-4a62-b087-aa3a92599c2a" />

### 1.2 pig avec nom de machine serveur
<img width="248" alt="image" src="https://github.com/user-attachments/assets/e3837b6b-7401-495e-b513-d0e340fb0908" />
pig avec nom de machine client

<img width="388" alt="image" src="https://github.com/user-attachments/assets/5f8db784-f9f7-4edc-acbb-f160c98d74ee" />
### 1.3 DANS LA MACHINE CLIENT
Sélectionnez l'interface réseau Ethernet.
Ouvrir les propriétés :
Cliquez sur Droite > Propriétés .
Sélectionnez "Protocole Internet version 4 (TCP/IPv4)" puis Propriétés .
Cocher :
✅ "Obtenir une adresse IP automatiquement"
✅ "Obtenir automatiquement l'adresse des serveurs DNS"
<img width="197" alt="image" src="https://github.com/user-attachments/assets/e3663511-ac30-4031-8968-d4e544529e52" />
puis, 
### 1.3 Modifie la configuration réseau du client pour qu'il soit en DHCP.
<img width="308" alt="image" src="https://github.com/user-attachments/assets/762a7dba-6a9e-48cd-8487-15af6eb26eb2" />
## pourquoi ne recuper pas les meme adress IP le client:
Le serveur DHCP attribue des adresses en fonction de son historique :
Si le client a déjà eu une adresse IP par le passé, le serveur essaie de lui réattribuer la même (tant qu'elle est libre).
Les baux DHCP ne sont pas libérés immédiatement :
Une adresse peut être considérée comme « réservée » pendant un certain temps après la fin de sa caution.
Les exclusions et réservations :
Certaines adresses peuvent être exclues de l'attribution ou réservées à des appareils spécifiques.
L'ordre de distribution n'est pas toujours séquentiel :
Le serveur DHCP peut attribuer des adresses en fonction de divers critères internes, notamment la charge ou des préférences de configuration.
<img width="374" alt="image" src="https://github.com/user-attachments/assets/4efb811d-acd3-4154-bdec-c44e577bfdc6" />
### 1.4 Est-ce que ce client peut avoir l'adresse IP 172.16.10.15 en DHCP ?
oui 
les etendues de DHCP est avec de pools 172.16.10.1 Jusqu'a 172.16.10.254
<img width="292" alt="image" src="https://github.com/user-attachments/assets/b7c80504-6ef0-4198-96e2-3a41d933e53d" />

<img width="374" alt="image" src="https://github.com/user-attachments/assets/c3eb7548-1932-4ca3-b0dd-1b7f0c267e17" />
#### capture de la machine client 
<img width="321" alt="image" src="https://github.com/user-attachments/assets/cd20a5a0-11b4-4b5b-9f9e-11f20a0a37df" />





