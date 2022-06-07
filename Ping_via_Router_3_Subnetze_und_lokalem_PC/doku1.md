
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



