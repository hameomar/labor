Labor 4
_______________________________
Subnetze:

A

X=24+ POSITION IN KLANNENLISTE

192.168.42.0/24


B

192+ POSITION

192.168.210.0/24


D

224 + POSITION

192.168.242.0/24

C

192.168.111.0/30

E

192.168.222.0/30
____________________________

Andorderungen:

-Netz C,E haben eine Maske /30
-Auf R1 ist für Netz B und D nur eine Route eingetragen
-Auf R1 ist keine Default Route eingetragen
-Auf dem eigenen Laptop/PC sind nur zwei zusätzliche Routen eingetragen
-Alle Subnetze sind klar vermerkt und Abgrenzungen sind grafisch erkennbar
-All PC können alle anderen anpingen
-Alle VPCS sind vom eigenen Laptop/PC anpingbar.
-In jedem Netz hat es ein VPCS mit einer Host Adresse aus dem entsprechenden Subnetz.


______________________________




R1 Konfiguration:

-Auf R1 ist für Netz B und D nur eine Route eingetragen:

![grafik](https://user-images.githubusercontent.com/102586033/173422643-bed7fc16-d4db-4e6e-8e55-9ae3aabd1646.png)


ip address add address=192.168.23.1/24 interface=ether1
ip address add address=192.168.42.1/24 interface=ether2
ip address add address=192.168.111.1/30 interface=ether3

![grafik](https://user-images.githubusercontent.com/102586033/173246172-23f74adf-b391-4106-8829-318cf6d1c743.png)



Rotuing zwischen Netzwerke einrichten:

ip route add dst-address=192.168.192.0/18 gateway=192.168.111.1

![grafik](https://user-images.githubusercontent.com/102586033/173422457-31675756-0697-4e4d-934f-eca29a511407.png)


PC1:


![grafik](https://user-images.githubusercontent.com/102586033/173246248-c9e63feb-d397-4237-8bb1-1227400dcc34.png)

_____________________

R2 Konfiguration:

ip address add address=192.168.210.1/24 interface=ether2
ip address add address=192.168.111.2/30 interface=ether3
ip address add address=192.168.222.1/30 interface=ether4


![grafik](https://user-images.githubusercontent.com/102586033/173246298-869aee63-f3dd-4117-9827-0dea0af02e98.png)


PC2:

![grafik](https://user-images.githubusercontent.com/102586033/173246345-8ca77c39-8cc7-4d28-b66b-3df2b3a39171.png)



Rotuing zwischen Netzwerke einrichten:

ip route add dst-address=192.168.42.1/24 gateway=192.168.111.1
ip route add dst-address=192.168.242.1/24 gateway=192.168.222.2


![grafik](https://user-images.githubusercontent.com/102586033/173422975-6b74b0d0-9a4f-4b27-9ca3-96a71b172335.png)

_____________________________

R3 Konfiguration:

ip address add address=192.168.242.1/24 interface=ether2
ip address add address=192.168.111.2/30 interface=ether4

![grafik](https://user-images.githubusercontent.com/102586033/173423351-3e962c99-4f5a-4ef2-b2e5-5e07c977b289.png)


Rotuing zwischen Netzwerke einrichten:

ip route add dst-address=192.168.42.0/24 gateway=192.168.111.1
ip route add dst-address=192.168.111.0/30 gateway=192.168.222.1
ip route add dst-address=192.168.210.0/24 gateway=192.168.222.1



![grafik](https://user-images.githubusercontent.com/102586033/173423343-d645759f-452a-43a1-a292-3cf0e1e116fc.png)


PC3:

![grafik](https://user-images.githubusercontent.com/102586033/173246446-2557b32d-fca0-4ff6-a264-3937ae60d37f.png)


