
ping mit Router

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

Router konfigurieren:

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

ip add 192.168.23.1 255.255.255.0

ip address add address=192.168.23.1/24 interface=ether1

ip address add address=192.168.28.1/24 interface=ether2

ip address add address=192.168.255.1/30 interface=ether3


![grafik](https://user-images.githubusercontent.com/102586033/172323345-f2eee974-a169-4f76-895f-bda61f11d7fd.png)



R2:

system identity set name=R2


ip address add address=192.168.255.1/24 interface=ether3


ip address add address=192.168.38.1/30 interface=ether2


![grafik](https://user-images.githubusercontent.com/102586033/172323536-eb439ac6-6ec8-46b6-a002-a40925e958b9.png)



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







