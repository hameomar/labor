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

*Auf R1 ist für Netz B und D nur eine Route eingetragen:


Supernet finden:

110000001010100011 01001000000000

110000001010100011 11001000000000


/18

neue IP :192.168.192.0


Supernetting ist die Methode zur Kombination von zwei oder mehr zusammenhängenden Netzwerkadressräumen, um einen einzigen, größeren Adressraum zu simulieren. Beim Supernetting fügen wir Bits aus dem Netzwerkteil zum Hostteil hinzu. 


______________

R1 IP Route 

ip route add dst-address=192.168.192.0/18 gateway=192.168.111.1

![grafik](https://user-images.githubusercontent.com/102586033/173422457-31675756-0697-4e4d-934f-eca29a511407.png)


![grafik](https://user-images.githubusercontent.com/102586033/173507904-726e0b1d-e68c-4657-af57-274f4fedee8f.png)


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


_________________
Erreichbarkeit (Pingen)

PC1

![grafik](https://user-images.githubusercontent.com/102586033/173425046-3b541c11-0152-46c8-adfb-dc1e1fcf7558.png)


PC2

![grafik](https://user-images.githubusercontent.com/102586033/173425177-1f4f7389-b80e-425c-8be5-01ee07735c86.png)



PC3

![grafik](https://user-images.githubusercontent.com/102586033/173425321-dd5b5f6a-596c-4e5d-ae01-d6c2a988931a.png)


![grafik](https://user-images.githubusercontent.com/102586033/173425397-71fd3cb2-c834-44ad-93fd-7ddc6a37ab5e.png)


_______________

Pingen vom lokalen eigenen Laptop auf Labor PCs:

Hier müssen wir eine Route auf unserem Computer über cmd oder Powershell hinzufügen und dann sollte es funktionieren:

Alle mögliche Netwerk-Route eingefügt:

![grafik](https://user-images.githubusercontent.com/102586033/173439861-da6a8977-3bc0-4f3d-b23b-bde504d4fb26.png)


![grafik](https://user-images.githubusercontent.com/102586033/173440032-baa11eb9-5938-4714-afb4-d29151f5cecd.png)


![grafik](https://user-images.githubusercontent.com/102586033/173440196-bfcf1ce1-610f-4b86-9793-f80ddd7ee365.png)


Es gibt immer wieder Problme beim Pingen auf Labor PCs. Ich habe es versucht, mit einem Backloop Adapter einzurichten und es geht gut und ich weiss aber nicht, ob das gut ist:

![grafik](https://user-images.githubusercontent.com/102586033/173443539-29179eb7-2bec-437d-a6a9-5f3ed5bb1536.png)



Die Datei:

[Labor4.zip](https://github.com/hameomar/labor/files/8894455/Labor4.zip)

