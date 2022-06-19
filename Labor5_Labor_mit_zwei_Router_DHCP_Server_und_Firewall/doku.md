Labor 5 - zwei Router, DHCP Server und Firewall
_______________________

Anforderungen:

Mind 2 /24 Subnetze (Netz A und Netz B)

Netz A: 192.168.50.0/24

X = 32 + Position in Klassenliste 18 = 50 

Netz B: 192.168.51.0/24

X = 33 + Position in Klassenliste 18

Jeweils ein DHCP Server für Subnetze A und B

PC1 bis PC4 erhalten IP Adresse via DHCP

Jeder PC kann alle anderen PCs und Router anpingen

Router haben immer die erste Host-Adresse (Host-min)

Kommunikation zwischen R1 und R2 erfolgt via Subnetz C

Subnetz C muss Maske /30 haben.

R1 und R2 sind via Laptop des Lernenden erreichbar.

Eine Firewallregel verhindert, dass PC1 und PC2 vom Subnetz 192.168.23.0/24 angepingt werden können.

Auf die Webinterfaces von R1 und R2 kann vom eigenen Laptop/PC zugegriffen werden

Alle Subnetze sind klar vermerkt und Abgrenzungen grafisch erkennbar
______________________

Netz A: 192.168.50.0/24

Netz B: 192.168.51.0/24

Netz C: 192.168.111.0/30

![grafik](https://user-images.githubusercontent.com/102586033/174460428-4cf96777-54e9-48ea-a383-3b38802badf3.png)


______________________


Router R1 und R2 Interface Konfiguration:

R1:

ip add add address=192.168.50.1/24 interface=ether3

ip add add address=192.168.50.2/24 interface=ether2

ip add add address=192.168.111.1/30 interface=ether4



![grafik](https://user-images.githubusercontent.com/102586033/174460560-881cefa6-d451-4b7a-8097-d78dc4b7d279.png)

![grafik](https://user-images.githubusercontent.com/102586033/174460622-84e9c9c1-0466-4471-811a-4b4146bf4e91.png)


R2:


 ip add add address=192.168.51.1/24 interface=ether2

 ip add add address=192.168.51.2/24 interface=ether3

 ip add add address=192.168.111.2/30 interface=ether4


![grafik](https://user-images.githubusercontent.com/102586033/174460608-db97cb33-641f-498b-8a28-b106752f176e.png)

____________________

Kommunikation zwischen R1 und R2 erfolgt via Subnetz C:

Damit die Kommunikation zwischen diesen beiden Netzen über das Netz C erfolgen kann, müssen wir eine statische Route über das Netz C zu R1 und R2 konfigurieren.
Zunächst stelle ich sicher, dass es keine statische Route via 192.168.23.0/24 eingerichtet wurde. Danach konfiguriere ich eine statische Route zwischen Netz A und B

![grafik](https://user-images.githubusercontent.com/102586033/174460742-96b99787-ca99-43bf-94fa-0d20ae81d5d8.png)


![grafik](https://user-images.githubusercontent.com/102586033/174460746-df9476f1-9775-43eb-86c8-6ab1a0acc942.png)


![grafik](https://user-images.githubusercontent.com/102586033/174460821-d6823a84-c96c-407c-83a3-c83ff9371a47.png)


______________________

