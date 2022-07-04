# Labor 6


________________
# Anforderungen:

PC1 und PC2 verwenden dasselbe Subnetz

Auf R1 und R2 ist DHCP aktiviert

PC1 und PC2 können ins Internet pingen

PC1 und PC2 können DNS auflösen (z.B. ping google.ch)

Alle Subnetze sind klar vermerkt und Abgrenzungen sind grafisch erkennbar.

MGMT Netz wird NUR für Management verwenden (Bei DHCP-Client für eth1 "Add Default Route" deaktivieren)

_______________
# Zeichnen:

![grafik](https://user-images.githubusercontent.com/102586033/177206376-07b1abbb-e53e-4ec7-98c9-27414cfca85a.png)

_____________________
# R1 (Core) Cofiguration:


[admin@Core] > ip route print

Flags: D - DYNAMIC; A - ACTIVE; c, s, y - COPY

Columns: DST-ADDRESS, GATEWAY, DISTANCE

     DST-ADDRESS       GATEWAY        DISTANCE

0  As 0.0.0.0/0         192.168.122.1         1

DAc 172.16.28.0/30    ether3                0

DAc 172.16.28.4/30    ether4                0

1  As 192.168.18.0/24   172.16.28.2           1

DAc 192.168.122.0/24  ether2                0

DAc 192.168.192.0/29  ether1                0

[admin@Core] > ip add print

Columns: ADDRESS, NETWORK, INTERFACE

 ADDRESS            NETWORK        INTERFACE

0 192.168.122.25/24  192.168.122.0  ether2

1 172.16.28.5/30     172.16.28.4    ether4

2 172.16.28.1/30     172.16.28.0    ether3

3 192.168.192.1/29   192.168.192.0  ether1


![grafik](https://user-images.githubusercontent.com/102586033/177210618-64dec511-7bec-483e-aa97-f32f9a2df554.png)





# NAT Configuration:

NAT steht für Network Address Translation. Es ist eine Möglichkeit, mehrere lokale private Adressen auf eine öffentliche Adresse abzubilden, bevor die Informationen übertragen werden. Unternehmen, die möchten, dass mehrere Geräte eine einzige IP-Adresse verwenden, nutzen NAT, ebenso wie die meisten Heimrouter.


Source-NAT
Masquerade.

Firewall NAT action=masquerade ist eine einzigartige Unterversion von action=srcnat, sie wurde speziell für den Einsatz in Situationen entwickelt, in denen sich die öffentliche IP-Adresse zufällig ändern kann, z.B. wenn der DHCP-Server sie ändert oder der PPPoE-Tunnel nach der Trennung eine andere IP-Adresse erhält, kurz gesagt - wenn die öffentliche IP-Adresse dynamisch ist.

Jedes Mal, wenn die Schnittstelle getrennt wird und/oder ihre IP-Adresse sich ändert, löscht der Router alle Einträge zur Verfolgung der maskierten Verbindung, die Pakete über diese Schnittstelle senden, und verbessert so die Wiederherstellungszeit des Systems nach einer Änderung der öffentlichen IP-Adresse.


srcnat NAT

Diese Art von NAT wird auf Pakete angewandt, die aus einem natted network stammen. Ein NAT-Router ersetzt die private Quelladresse eines IP-Pakets durch eine neue öffentliche IP-Adresse, während es den Router durchläuft. Der umgekehrte Vorgang wird auf die Antwortpakete angewandt, die in die andere Richtung reisen.





[admin@Core] > ip firewall/nat/print

Flags: X - disabled, I - invalid; D - dynamic

0    chain=srcnat action=masquerade out-interface=ether2 log=no log-prefix=""

[admin@Core] >


![grafik](https://user-images.githubusercontent.com/102586033/177206617-a60ded08-58d4-4848-90a7-2f3a87ae036f.png)


![grafik](https://user-images.githubusercontent.com/102586033/177209183-a301c920-d275-4a14-bf09-d2d8c3f92a08.png)




# DHCP Server Konfiguration:

Auf Core R1 habe ich den DHCP Server konfiguriert. Auf R2 und R3 habe ich je ein DHCP Relay.
Ein DHCP-Relay-Agent ist ein Host oder Router, der DHCP-Pakete zwischen Clients und Servern weiterleitet. Netzwerkadministratoren können den DHCP-Relay-Dienst der SD-WAN-Appliances nutzen, um Anfragen und Antworten zwischen lokalen DHCP-Clients und einem entfernten DHCP-Server weiterzuleiten.

![grafik](https://user-images.githubusercontent.com/102586033/177206798-d35bccfd-39ca-4397-a3fe-fcb602a66451.png)


![grafik](https://user-images.githubusercontent.com/102586033/177206930-aa975da5-c2ce-4753-a4a2-5246776c57ad.png)

![grafik](https://user-images.githubusercontent.com/102586033/177207119-b2b5da68-9fe2-4db7-bb68-667783b7f3e2.png)


_____________
# R2 Conifguration:


[admin@R2] > ip route print

Flags: D - DYNAMIC; A - ACTIVE; c, s, y - COPY

Columns: DST-ADDRESS, GATEWAY, DISTANCE

     DST-ADDRESS       GATEWAY      DISTANCE

0  As 0.0.0.0/0         172.16.28.1         1

DAc 172.16.28.0/30    ether2              0

1  As 172.16.28.4/30    172.16.28.1         1

DAc 192.168.18.0/24   ether3              0

2  As 192.168.122.0/24  172.16.28.1         1

DAc 192.168.192.0/29  ether1              0

[admin@R2] > ip add print

Columns: ADDRESS, NETWORK, INTERFACE

 ADDRESS           NETWORK        INTERFACE

0 192.168.192.2/29  192.168.192.0  ether1

1 192.168.18.1/24   192.168.18.0   ether3

2 172.16.28.2/30    172.16.28.0    ether2

[admin@R2] >

![grafik](https://user-images.githubusercontent.com/102586033/177208193-96f0c9b5-43b9-4cad-8a61-a3ca73233aad.png)

# DHCP RELAY

![grafik](https://user-images.githubusercontent.com/102586033/177208292-1c9b819d-8278-4633-86c7-ffe2bcc85940.png)


_______________

# R3 Konfiguration:

![grafik](https://user-images.githubusercontent.com/102586033/177208388-8fbb3c99-88b1-430d-8944-f8ba4431aac5.png)


[admin@R3] > ip add print

Columns: ADDRESS, NETWORK, INTERFACE

 ADDRESS           NETWORK        INTERFACE

0 192.168.192.3/29  192.168.192.0  ether1

1 172.16.28.6/30    172.16.28.4    ether2

2 192.168.18.3/24   192.168.18.0   ether3

[admin@R3] > ip route print

Flags: D - DYNAMIC; A - ACTIVE; c, s, y - COPY

Columns: DST-ADDRESS, GATEWAY, DISTANCE

    DST-ADDRESS       GATEWAY      DISTANCE

0  As 0.0.0.0/0         172.16.28.5         1

1  As 172.16.28.0/30    172.16.28.5         1

DAc 172.16.28.4/30    ether2              0

DAc 192.168.18.0/24   ether3              0

2  As 192.168.122.0/24  172.16.28.5         1

DAc 192.168.192.0/29  ether1              0

[admin@R3] >


# DHCP RELAY

![grafik](https://user-images.githubusercontent.com/102586033/177208528-5b250c46-6c4d-4d55-8dbc-b01427361295.png)

_________

PC1 und PC2 können DNS auflösen/ 8.8.8.8 und sich gegenseitig anpingen und verwenden dieselbe Subnet:

![grafik](https://user-images.githubusercontent.com/102586033/177208814-956a91c3-1357-493c-b881-dc414287c773.png)


![grafik](https://user-images.githubusercontent.com/102586033/177207333-3b4e06d4-9fa2-420a-a095-587d6f184da4.png)


__________________


# MGMT1 NETZ wird nur für Managment verwendet.
/29 Subnet verwendet

![grafik](https://user-images.githubusercontent.com/102586033/177208980-4b614311-ba7f-40b3-a80a-bc76d789ba7f.png)

Das Häkchen ist nicht eingesetzt.

______________

# Alle Routers können sich gegenseitig anpingen


 ![grafik](https://user-images.githubusercontent.com/102586033/177210930-700c6b4d-c785-4f1e-a005-ff4e3332eca6.png)


![grafik](https://user-images.githubusercontent.com/102586033/177210944-759efeee-5861-4a62-b9b0-c15bef6e7a61.png)


 
 

 
