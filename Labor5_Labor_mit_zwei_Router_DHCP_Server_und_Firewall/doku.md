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
_____________________

Default Route:Weil wir CLoud eingefügt haben.

Default-Route

Die Route mit der dst-Adresse 0.0.0.0/0 gilt für jede Zieladresse. Eine solche Route wird als Standard-Route bezeichnet. Wenn die Routing-Tabelle eine aktive Standard-Route enthält, wird die Suche in der Routing-Tabelle niemals fehlschlagen. 

R1

![grafik](https://user-images.githubusercontent.com/102586033/174672255-e4837fd8-b272-48e4-b056-f0e13b14e450.png)

R2

![grafik](https://user-images.githubusercontent.com/102586033/174672398-abfb6e61-fd4e-41d1-95d3-80f99f599d5b.png)


______________


_______________

______________________
Jeweils ein DHCP Server für Subnetze A und B .PC1 bis PC4 erhalten IP Adresse via DHCP:

DHCP:

Das Dynamic Host Configuration Protocol (DHCP) ist ein Client/Server-Protokoll, das einem Internet Protocol (IP)-Host automatisch seine IP-Adresse und andere zugehörige Konfigurationsinformationen wie die Subnetzmaske und das Standard-Gateway liefert. 

Wir durfen nicht, 2 DHCP Server in einem Netzwerk auf einem Router erstellen. Wir können 2 Pools "Ranges" erstellen und die beide Interfaces Ether1 und Ether2 als DHCP Client einstellen, damit sie die IPs verteilen/zuweisen können:

_________________________
Update für die Konfiguration:



ether1= 192.168.50.1

ip pool add range=192.168.50.1-192.168.50.127 name=range1

ip dhcp-server add name=range1 address-pool=range1 interface=ether3

ip dhcp-server network add address=192.168.50.0/24 gateway=192.168.50.1 dns-server=8.8.8.8

ip dhcp-server enable number=range1
__________________

ether 2 = 192.168.50.2

ip pool  add range=192.168.50.128-192.168.50.254 name=range2

ip dhcp-server add name=range2 address-pool=range2 interface=ether2

ip dhcp-server enable number=range2

DHCP Client > ether1 und ehter1 einfügen, damit die beide IPS zuweisen können:


![grafik](https://user-images.githubusercontent.com/102586033/175834925-16833666-64a4-4629-a3aa-3e6a5f34c7d6.png)



![grafik](https://user-images.githubusercontent.com/102586033/175834932-c38edad1-f17c-4020-bad3-922e232b38fc.png)


![grafik](https://user-images.githubusercontent.com/102586033/175834940-7c27ebd4-45da-41d3-af75-31d13ba2da33.png)



![grafik](https://user-images.githubusercontent.com/102586033/175834954-e3031211-d950-49d7-9d2c-e76479406d19.png)




_______________________

R1:

ip dhcp-server/ setup

Select interface to run DHCP server on

dhcp server interface: ether1

Select network for DHCP addresses

dhcp address space: 192.168.50.0/24

Select gateway for given network

gateway for dhcp network: 192.168.50.1

Select pool of ip addresses given out by DHCP server

ich werde die Adressen 192.168.50.1 und 192.168.50.2 für die beide Interfaces statisch festlegen.

addresses to give out: 192.168.50.3-192.168.50.254

Select DNS servers

dns servers: 192.168.50.1

Select lease time

lease time: 3d


![grafik](https://user-images.githubusercontent.com/102586033/174498426-94a709d6-4120-412a-a660-b581a722f8f0.png)

Interface ether2 ist mit dem DHCP Server nicht verbunden und ich werde den Pool zu Interface Ether2 auch zuweisen und danach kann PC2 eine IP Adresse vom DHCP Server bekommen:


/ip/dhcp-server>  add interface=ether2 address-pool=dhcp_pool0 


![grafik](https://user-images.githubusercontent.com/102586033/174499819-5ba866eb-676a-4a33-9178-3c1b3f3d5257.png)

______________________

PC 1 und PC2 haben IP vom DHCP Server bekommen:

![grafik](https://user-images.githubusercontent.com/102586033/174500057-2d4f82ab-f406-4ffd-9bbd-d4ca97a94fcc.png)


______________________

R2 :

[admin@MikroTik] /ip/dhcp-server> setup
Select interface to run DHCP server on

dhcp server interface: ether2 ether1
input does not match any value of interface
dhcp server interface: ether2, ether1
input does not match any value of interface
dhcp server interface: ether2
Select network for DHCP addresses

dhcp address space: 192.168.51.0/24
Select gateway for given network

gateway for dhcp network: 192.168.51.1
Select pool of ip addresses given out by DHCP server

addresses to give out: 192.168.51.1-192.168.51.254
Select DNS servers

dns servers: 8.8.8.8
Select lease time

lease time: 3d

![grafik](https://user-images.githubusercontent.com/102586033/174500128-a397f40d-4604-40d7-9d63-1af10299cb40.png)


Interface 3 zum Pool einfügen:

add interface=ether3 address-pool=dhcp_pool0 lease-time 3d


![grafik](https://user-images.githubusercontent.com/102586033/174500201-c9c2dde6-b9c4-49f8-989c-389857a74d68.png)

_________________
PC 3 und PC 4 haben IPs vom DHCP Server bekommen:

![grafik](https://user-images.githubusercontent.com/102586033/174500236-cb2253b7-ba2c-4eb9-b806-2af35c5b7651.png)






_____________________

pingen:

![grafik](https://user-images.githubusercontent.com/102586033/174461150-6147e4e3-8e67-4eb6-8644-c23d42c025e0.png)


______________



R1 kann Router 2 anpingen und umgekehrt

![grafik](https://user-images.githubusercontent.com/102586033/174675639-529f7d03-d684-435c-84c6-0849f5299866.png)



