Labor 6


________________
Anforderungen:

PC1 und PC2 verwenden dasselbe Subnetz

Auf R1 und R2 ist DHCP aktiviert

PC1 und PC2 können ins Internet pingen

PC1 und PC2 können DNS auflösen (z.B. ping google.ch)

Alle Subnetze sind klar vermerkt und Abgrenzungen sind grafisch erkennbar.

MGMT Netz wird NUR für Management verwenden (Bei DHCP-Client für eth1 "Add Default Route" deaktivieren)

_______________
Zeichnen:

![grafik](https://user-images.githubusercontent.com/102586033/177206376-07b1abbb-e53e-4ec7-98c9-27414cfca85a.png)

_____________________
R1 (Core) Cofiguration:


[admin@Core] > ip add print

Columns: ADDRESS, NETWORK, INTERFACE

# ADDRESS            NETWORK        INTERFACE

0 192.168.122.25/24  192.168.122.0  ether2

1 172.16.28.5/30     172.16.28.4    ether4

2 172.16.28.1/30     172.16.28.0    ether3

3 192.168.192.1/29   192.168.192.0  ether1

[admin@Core] > ip route print

Flags: D - DYNAMIC; A - ACTIVE; c, s, y - COPY

Columns: DST-ADDRESS, GATEWAY, DISTANCE

#     DST-ADDRESS       GATEWAY        DISTANCE

0  As 0.0.0.0/0         192.168.122.1         1

DAc 172.16.28.0/30    ether3                0

DAc 172.16.28.4/30    ether4                0

DAc 192.168.122.0/24  ether2                0

DAc 192.168.192.0/29  ether1                0

[admin@Core] >


![grafik](https://user-images.githubusercontent.com/102586033/177206457-5688ca71-d28e-4d1f-b047-cea9d2dd4a33.png)


NAT Config:



[admin@Core] > ip firewall/nat/print

Flags: X - disabled, I - invalid; D - dynamic

0    chain=srcnat action=masquerade out-interface=ether2 log=no log-prefix=""

[admin@Core] >


![grafik](https://user-images.githubusercontent.com/102586033/177206617-a60ded08-58d4-4848-90a7-2f3a87ae036f.png)


DHCP Server Konfiguration:

Auf Core R1 habe ich den DHCP Server konfiguriert. Auf R2 und R3 habe ich je ein DHCP Relay.
Ein DHCP-Relay-Agent ist ein Host oder Router, der DHCP-Pakete zwischen Clients und Servern weiterleitet. Netzwerkadministratoren können den DHCP-Relay-Dienst der SD-WAN-Appliances nutzen, um Anfragen und Antworten zwischen lokalen DHCP-Clients und einem entfernten DHCP-Server weiterzuleiten.

![grafik](https://user-images.githubusercontent.com/102586033/177206798-d35bccfd-39ca-4397-a3fe-fcb602a66451.png)


![grafik](https://user-images.githubusercontent.com/102586033/177206930-aa975da5-c2ce-4753-a4a2-5246776c57ad.png)

![grafik](https://user-images.githubusercontent.com/102586033/177207119-b2b5da68-9fe2-4db7-bb68-667783b7f3e2.png)


_____________
R2 Conifguration:




_________


![grafik](https://user-images.githubusercontent.com/102586033/177207333-3b4e06d4-9fa2-420a-a095-587d6f184da4.png)



