
# Labor 6 

 Korrektur gemäß den Anweisungen des Lehrers (DHCP ohne DHCP-Relay, mit 2 DHCP-Servern, wobei jeder Server seinen eigenen IP-Pool hat)
 
DHCP Adress Pool: Ein Netzwerkprotokoll, das es einem Server ermöglicht, einem IP-fähigen Gerät automatisch eine IP-Adresse aus einem definierten Bereich von Nummern zuzuweisen, die für ein bestimmtes Netzwerk konfiguriert sind.

# Lehrer Kommentare

1-Bei einem Router ist die Routing Tabelle die wichtigste Element, was man ganz korrekt konfigurierem muss

2-Wir haben im M123 "Server Dienste in Betrib nehmen" gelernt, dass wenn wir 2 DHCP Servern haben, müssen wir einen als Master festlegen.

* 
 Wenn Sie DHCP in einem Netzwerk mit mehreren Segmenten verwenden möchten, müssen Sie entweder einen DHCP-Server oder einen Relay-Agenten in jedem Segment einsetzen oder sicherstellen, dass Ihr Router Bootstrap Protocol (BOOTP) Broadcasts weiterleiten kann. Das Problem mit einem DHCP-Relay besteht darin, dass die Cleints keine IP erhalten, wenn beispielsweise ein Netzwerk auf dem Weg zum Zielnetzwerk ausgefallen ist. In diesem Labor werde ich daher R2 mit R3 verbinden, und wenn ein Netzwerk 172.16.28.0/30 oder 172.16.28.4/30 ausgefallen ist, wird der andere Router die IP-Zuweisung übernehmen.
 
 
 __________

![grafik](https://user-images.githubusercontent.com/102586033/178100161-37ece9eb-dbab-4749-bd2d-679556aab032.png)


__________

# R1 (Core) Konfiguration:

# Interfaces IP


[admin@Core] > ip add print

Columns: ADDRESS, NETWORK, INTERFACE

ADDRESS            NETWORK        INTERFACE

0 192.168.122.25/24  192.168.122.0  ether2

1 172.16.28.5/30     172.16.28.4    ether4

2 172.16.28.1/30     172.16.28.0    ether3

3 192.168.192.1/29   192.168.192.0  ether1

[admin@Core] >

![grafik](https://user-images.githubusercontent.com/102586033/178100582-45d08c58-c06a-4a9a-935b-77f915eba4b1.png)


# Routing Tabelle

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

[admin@Core] >


![grafik](https://user-images.githubusercontent.com/102586033/178100665-5c848b1f-abd3-4ba8-a1de-b7ef116ac4b1.png)

# Zugang Zum Internet / NAT Role:

[admin@Core] > ip firewall/nat/print

Flags: X - disabled, I - invalid; D - dynamic

0    chain=srcnat action=masquerade out-interface=ether2

[admin@Core] >

![grafik](https://user-images.githubusercontent.com/102586033/178101140-d6d62dc5-3822-4441-b672-7d419f662345.png)


______________________

# R2 Konfiguration:

IP Interfaces:

![grafik](https://user-images.githubusercontent.com/102586033/178101149-d829fe9f-88d2-44dd-8258-021f68a6dcdc.png)


[admin@R2] > ip add print

Columns: ADDRESS, NETWORK, INTERFACE

ADDRESS           NETWORK        INTERFACE

0 192.168.192.2/29  192.168.192.0  ether1

1 192.168.18.1/24   192.168.18.0   ether3

2 172.16.28.2/30    172.16.28.0    ether2

[admin@R2] >

# R2 IP Route :

![grafik](https://user-images.githubusercontent.com/102586033/178101231-9c038efc-4ecb-49f6-a58d-1152cbb5d9e4.png)



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

[admin@R2] >

# R2 DHCP Server / Ip Pool Konfiguration:


![grafik](https://user-images.githubusercontent.com/102586033/178101307-6ed9d4c7-4bef-429b-b7e6-86805a6cf733.png)



[admin@R2] > ip pool/print

Columns: NAME, RANGES

NAME        RANGES

0  dhcp_pool1  192.168.18.2-192.168.18.127

[admin@R2] > ip dhcp-server/print

Columns: NAME, INTERFACE, ADDRESS-POOL, LEASE-TIME

NAME   INTERFACE  ADDRESS-POOL  LEASE-TIME

0 dhcp1  ether3     dhcp_pool1    1w1d

[admin@R2] >

______________

# R3 Konfiguration :

IP Interfaces:

![grafik](https://user-images.githubusercontent.com/102586033/178101377-6a275824-d043-4b34-8ad3-8e3c54f12bb8.png)


[admin@R3] > ip add print

Columns: ADDRESS, NETWORK, INTERFACE

ADDRESS            NETWORK        INTERFACE

0 192.168.192.3/29   192.168.192.0  ether1

1 172.16.28.6/30     172.16.28.4    ether2

2 192.168.18.128/24  192.168.18.0   ether3

[admin@R3] >


Routing Tabelle:

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


![grafik](https://user-images.githubusercontent.com/102586033/178101491-d49e404f-fb7b-4808-a2b5-b73011b48dda.png)


# R3 DHCP Server / Ip Pool Konfiguration :

[admin@R3] > ip pool/print

Columns: NAME, RANGES

  NAME    RANGES

0  range2  192.168.18.129-192.168.18.254

[admin@R3] > ip dhcp-server/print

Columns: NAME, INTERFACE, ADDRESS-POOL, LEASE-TIME

 NAME   INTERFACE  ADDRESS-POOL  LEASE-TIME

0 dhcp1  ether3     range2        1w1d

[admin@R3] >

![grafik](https://user-images.githubusercontent.com/102586033/178101574-dce08ad1-daec-4784-a7b7-0f8787d778bc.png)


_________________



