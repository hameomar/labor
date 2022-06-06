ping mit Router

Aufgabe Link:

https://gitlab.com/ch-tbz-it/Stud/m129/-/tree/main/07_GNS3_Labore#2-labor-2-ping-mit-router

Anforderungen

Zwei unterschiedliche /24 Subnetze

Router hat jeweils erste IPv4-Adresse

PC1, PC2 und PC3 haben jeweils eine statische IPv4-Adresse

Alle PCs können sich gegenseitig anpingen

![grafik](https://user-images.githubusercontent.com/102586033/172234043-75fb0a31-1121-4310-b08f-16f18f5b0a32.png)

_______________________

Die zwei unetrschiedlich Subnetze:

Netzwerk Links:

192.168.1.0/24


Netzwerkadresse:	192.168.1.0

Gateway: 192.168.1.1

Verwendbarer Host-IP-Bereich:	192.168.1.1 - 192.168.1.254

Broadcast-Adresse:	192.168.1.255

Gesamtzahl der Hosts:	256

Anzahl der nutzbaren Hosts:	254

Subnetmask: 255.255.255.0
__________________________

Netzwerk Recht:

192.168.2.0/24


Netzwerkadresse:	192.168.2.0

Gateway: 192.168.2.1

Verwendbarer Host-IP-Bereich:	192.168.2.1 - 192.168.2.254

Broadcast-Adresse:	192.168.2.255

Gesamtzahl der Hosts:	256

Anzahl der nutzbaren Hosts:	254

Subnetmask: 255.255.255.0

::::::::::::::::::::::::::::::::::::::::::::::

Grundlegende Bedienung eines MikroTik Routers:

![grafik](https://user-images.githubusercontent.com/102586033/172236300-4a1e6a1e-c1b4-41c1-9aaa-57ad7fc18c1e.png)


Enter drucken

![grafik](https://user-images.githubusercontent.com/102586033/172236370-607b056f-b533-4a1e-b4a6-8434733c0a07.png)


![grafik](https://user-images.githubusercontent.com/102586033/172236418-2b65b534-61a3-4459-ad47-2caae821df85.png)

ein neues PW festlegen:

![grafik](https://user-images.githubusercontent.com/102586033/172236668-a628bbbb-143d-4563-a425-522599ec2d4a.png)


![grafik](https://user-images.githubusercontent.com/102586033/172236761-b3214dbb-83b9-4083-9dee-c43443cdb366.png)

System identity:

Die Systemidentität ist ein eindeutiger Name, mit dem sich das System gegenüber anderen Routern im Netz identifiziert.

![grafik](https://user-images.githubusercontent.com/102586033/172237801-cffdb791-13a1-48f0-a6a9-0317e591d345.png)


Mit diesem Befehl kann ich einen neuen Name für Router festlegen:

system identity set name=R1 


![grafik](https://user-images.githubusercontent.com/102586033/172239004-d8448faf-7895-4780-bf83-9d6960801e8e.png)


____________________

Diagramm zeichnen und einen Interface eine IPv4-Adresse zuordnen:


![zecihnen](https://user-images.githubusercontent.com/102586033/172239971-e21d5f19-4b73-4e05-bdac-9a8b5359f6a0.jpg)


![grafik](https://user-images.githubusercontent.com/102586033/172241883-19dd0356-7cdf-490c-a689-d4575510b9fb.png)



ipv4 für Router Interfaces festlegen:


Netzwerk Links: Der Interface ether1  bekommt die erste IP Adresse in diesem Netzwerk:

192.168.1.1/24

Befehl :

ip address add address=192.168.1.1/24 interface=ether1

![grafik](https://user-images.githubusercontent.com/102586033/172247122-0bffc3c1-a642-4aea-9fea-58733f58679e.png)



Netzwerk Recht: Der Interface ether2  bekommt die erste IP Adresse in diesem Netzwerk:

192.168.2.1/24

ip address add address=192.168.2.1/24 interface=ether2

![grafik](https://user-images.githubusercontent.com/102586033/172247329-0ca0fc17-87a6-4fa5-95bb-b02ff97e8d26.png)

Konfiguration Speichern (Backup):

![grafik](https://user-images.githubusercontent.com/102586033/172248319-35268437-7c0c-438b-b01e-816d2966bb72.png)

/ip route 

print

![grafik](https://user-images.githubusercontent.com/102586033/172253138-19461980-7644-4332-8a27-04112480de47.png)


_____________________________
Statische IPV4 bei PC1 und PC2, PC3 festlegen:

Statische IP festlagen Usage: 

Ip subnetmask gateway

ip dns 192.168.x.1

PC 1:

ip 192.168.1.2 255.255.255.0 192.168.1.1

ip dns 192.168.1.1

show ip

![grafik](https://user-images.githubusercontent.com/102586033/172248992-b5c5ecf6-1a47-4dde-9b31-22ef6f694bd2.png)


PC 2:

ip 192.168.2.2 255.255.255.0 192.168.2.1

ip dns 192.168.2.1

show ip

![grafik](https://user-images.githubusercontent.com/102586033/172249180-d9add707-1031-4713-b447-ad76cd4b77c7.png)



PC 3:

ip 192.168.2.3 255.255.255.0 192.168.2.1

ip dns 192.168.2.1

show ip


![grafik](https://user-images.githubusercontent.com/102586033/172249328-816e5b29-ce26-4f18-8106-6b03e26fd568.png)


Config Save:

![grafik](https://user-images.githubusercontent.com/102586033/172249668-04f0b423-be46-4b10-941e-0d094d82a7f4.png)


______________________

Pingen


Alle PC können sich gegenseitig pingen



![ip](https://user-images.githubusercontent.com/102586033/172250923-db3a10f1-60a3-46e7-a566-d7ad20884a4c.jpg)



____________________

![grafik](https://user-images.githubusercontent.com/102586033/172253597-bf7ef5a5-a624-45f8-8da8-06b7da5079fc.png)



Datei:

[ping_mit_router.zip](https://github.com/hameomar/labor/files/8848117/ping_mit_router.zip)


