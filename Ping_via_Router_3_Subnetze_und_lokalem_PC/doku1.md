
Labor 3

_______________________

Aufgabe Link:
https://gitlab.com/ch-tbz-it/Stud/m129/-/tree/main/07_GNS3_Labore#2-labor-2-ping-mit-router


Anforderungen

-IPv4 Subnetz A ist wie folgt festgelegt: 192.168.28.0/24


-IPv4 Subnetz B wird wie Netz A festgelegt: 192.168.38.0/24


-PC2 kann PC1 anpingen und umgekehrt

-PC1 und PC2 sind vom eigenen Laptop/PC anpingbar.

-Netz C hat eine Maske /30

-Alle Subnetze sind klar vermerkt und Abgrenzungen grafisch erkennbar






![grafik](https://user-images.githubusercontent.com/102586033/172212957-d41289e8-3944-4665-ad43-17ceb9939dbc.png)


![grafik](https://user-images.githubusercontent.com/102586033/172215294-3564f369-2bb8-4e29-ae62-e9414875ca72.png)




_____________________________
IPv4 Subnetz A ist wie folgt bie mir festgelegt:

Position in Klassenliste: 18

192.168.X.0/24

X = 10 + Position in Klassenliste

192.168.28.0/24

Network ID : 192.168.28.0

Subnetmask: /24 

Gateway: 192.168.28.1

Host Range : 192.168.28.2 - 192.168.28.254

Broadcast : 192.168.28.255
_______________________________



IPv4 Subnetz B wird wie Netz A bei mir festgelegt:

Position in Klassenliste:18
 
X = 20 + Position in Klassenliste

192.168.38.0/24


Network ID : 192.168.38.0

Subnetmask: /24 

Gateway: 192.168.38.1

Host Range : 192.168.38.2 - 192.168.38.254

Broadcast : 192.168.38.255

___________________________________

IPv4 Subnetz C wird wie Netz A bei mir festgelegt:

*Es muss eine /30 Subnet Maske haben.

192.168.255.0/30

Network Address:	192.168.255.0

Host Range:	192.168.255.1 - 192.168.255.2

Broadcast Addresse :	192.168.255.3

Total Number of Hosts:	4

Number of Usable Hosts:	2

Subnet Mask:	255.255.255.252

_______________________________

Mikrotik Routers konfigurieren:

IP Address zu Interfaces zugweisen:

ip address add address=192.168.x.1/24 interface=etherx

Rotuing zwischen Netzwerke einrichten:

ip route add dst-address=(ZielNetzwerk/Mask) gateway=nexthop without mask

![grafik](https://user-images.githubusercontent.com/102586033/173229603-9876748c-6393-4690-9df1-dad7a98cdee2.png)

________________________________

non Mikrotik-Router konfigurieren:

en

config t

init interface-name

ip add 192.168.x.1 255.255.255.0

no shut

end

show ip int brief

show ip route

conf t

ip route (ip of ziel Netwerk 192.168.x.0) 255.255.255.0  (ip of next hop zum Ziel Netzwerk)


_________________________________


Diagramm zeichnen:

![grafik](https://user-images.githubusercontent.com/102586033/172315442-f0245dae-deec-41c8-aa13-0a7f3955f259.png)



____________________________________

Routers Konfigurieren:

R1:

system identity set name=R1


ip address add address=192.168.23.1/24 interface=ether1

ip address add address=192.168.28.1/24 interface=ether2

ip address add address=192.168.255.1/30 interface=ether3


![grafik](https://user-images.githubusercontent.com/102586033/172323345-f2eee974-a169-4f76-895f-bda61f11d7fd.png)

R1 Route Konfiguration

ip route add dst-address=192.168.23.0/24 gateway=192.168.23.1

ip route add dst-address=192.168.38.0/24 gateway=192.168.255.2

![grafik](https://user-images.githubusercontent.com/102586033/173505747-42a154ce-0957-4ff8-9e8b-944ea2ec97d2.png)



_____________________________________


R2:

system identity set name=R2


ip address add address=192.168.255.2/24 interface=ether3


ip address add address=192.168.38.2/30 interface=ether2


![grafik](https://user-images.githubusercontent.com/102586033/173229683-9892a577-17be-4028-aa06-48aa67c679a5.png)


R2 Route Konfiguration:

![grafik](https://user-images.githubusercontent.com/102586033/173505968-3da763ff-83e5-41ea-be82-afd8f230520c.png)


___________________________

IP Route Configuration:

Damit 2 verschiedene Netzwerke miteinander kommunizieren können, kann man eine statische Route konfigurieren:

Bei Mikrotik Routers ist der Befehl so:

ip route add dst-address=(ZielNetzwerk/Mask) gateway=nexthop without mask



![Screenshot 2022-06-12 130153](https://user-images.githubusercontent.com/102586033/173230039-5be205e6-c9d4-4071-8875-ef0cd18ef67d.jpg)


IP Route sieht bei R1 und R2 so aus:


![grafik](https://user-images.githubusercontent.com/102586033/173230093-5e7240bd-9715-4710-9970-b9ee7e31d401.png)





____________________________
PC1:

ip 192.168.28.2 255.255.255.0 192.168.28.1

ip dns 192.168.28.1

show ip

![grafik](https://user-images.githubusercontent.com/102586033/172321592-a17ec369-00b6-4505-b1b1-2da92d5543bd.png)


PC2:

ip 192.168.38.2 255.255.255.0 192.168.38.1

ip dns 192.168.38.1

show ip

![grafik](https://user-images.githubusercontent.com/102586033/172321744-73e0d0b7-7715-4e32-a50f-eacee50a252e.png)


_______________

Pingen


PC 1 mit PC 2 und gegenseitig:

![grafik](https://user-images.githubusercontent.com/102586033/173229764-869f9bdc-4da7-4299-b2c3-8f4be19a42dc.png)



PC 1 auf R2 / PC 2 auf R1:


![grafik](https://user-images.githubusercontent.com/102586033/173229861-ab4db504-a8e8-46eb-b848-c7e13c9cbe78.png)



Vom eigenen Laptop auf PC1 und PC pingen:

Routing Tabelle updaten:

![grafik](https://user-images.githubusercontent.com/102586033/173447449-f29baa9d-7505-4128-8885-cecf10fae738.png)


Das kann auch helfen:

![grafik](https://user-images.githubusercontent.com/102586033/173448242-abad6f66-fa42-4867-aff6-f7dfdff1225c.png)



![grafik](https://user-images.githubusercontent.com/102586033/173448434-d78aea44-6381-4331-96f6-ea6f6a23b203.png)





Die Datei

[Labor3_V2_Omar.zip](https://github.com/hameomar/labor/files/8894612/Labor3_V2_Omar.zip)



