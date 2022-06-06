 
Aufgabe Link:

https://gitlab.com/ch-tbz-it/Stud/m129/-/tree/main/07_GNS3_Labore#1-labor-1-ping-mit-switch

Anforderungen

PC1,PC2 und PC3 haben je eine statische IPv4-Adresse.
Alle PCs können sich gegenseitig anpingen.
Verwendetes Subnetz ist vermerkt.
Wireshark Packet Traces wurden durchgeführt (und sind dokumentiert!).
__________________________________________

Switch 

Ein Switch ist ein Kopplungselement, das mehrere Hosts in einem Netzwerk miteinander verbindet. In einem Ethernet-Netzwerk, das auf der Sterntopologie basiert, dient ein Switch als Verteiler für die Datenpakete. 
 
Layer 2 Switch vs Layer 3 
Der Unterschied zwischen einem Layer-2-Switch und einem Layer-3-Switch ist die Routing-Funktion. Ein Layer-2-Switch arbeitet nur mit MAC-Adressen.Ein Layer-3-Switch hingegen kann auch statisches Routing und dynamisches Routing durchführen, einschliesslich IP- und VLAN-Kommunikation (Virtual Local Area Network). 
 
Layer2 Switch 	Layer 3 Switch 
Dieser Switch arbeitet auf Layer 2 	Arbeitet auf Layer 3 
Arbeitet mit MAC Adressen 	Verwendet IPs und kann die Aufgabe eines Switches übernehmen  
 
 
Ping mit Switch via GNS3 
 
GNS3 wird von Netzwerkadministratoren verwendet, um virtuelle und reale Netzwerke zu emulieren, zu konfigurieren, zu testen und Fehler zu beheben. 
Mit Drag und Drop Funktionen kann man Geräten zu einem Workspace einfügen und konfigurieren, testen. 
 
Wir werden uns mit einem Remote Server verbinden, damit wir unsere Topologie zeichnen und testen können. Der Vorteil ist, dass man kein extra VMs für GNS3 braucht. 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172190626-5c5bc56a-26dc-41d4-a895-a2869875088c.png)

 
Ein Swicht verfügt über Interfaces und diese werden für "Geräte-Einschließen" genutzt. 
 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191016-3c90d122-c361-4620-9018-646796b6fdb8.png)

 
 Hinweis:
 können wir mit Layer 2 Switch pingen?
Nein. Auf Schicht 2 ist es nicht möglich, einen Rahmen an ein anderes Gerät zu senden und eine Antwort zu erwarten.

Auswahl eines Netzwerk: 
Wir haben bei diesem Labor 3 Geräten zu verbinden.
Das heisst wir brauchen 3 Bits. Mit 3 Bits bekommen wir 8 Adressen: 
IP Address:192.168.1.0 
Network Address:192.168.1.0 
Usable Host IP Range:192.168.1.1 - 192.168.1.6 
Broadcast Address:192.168.1.7 
Total Number of Hosts:8 
Number of Usable Hosts:6 
Subnet Mask:255.255.255.248 
Binary Subnet Mask:11111111.11111111.11111111.11111000 
IP Class:C 
CIDR Notation:/29 
 
192.168.1.0/29 
 
 
Jedoch wurde unseres Netzwerk bei dieser VPN Verbindung vorgegeben: 
 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191052-a29f3b83-2e8f-49b6-805f-38227204bf91.png)

 
 
Und deswegen werde ich diese Netzwerk verwenden, um mein Labor zu konfigurieren. 
 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191083-3c8d83ab-684d-4f89-b74f-5a61a8405226.png)

 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191182-f4ebd82a-030f-4275-b9b7-ad424e406a98.png)

 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191204-4e460f0b-6f20-4345-9cd8-9af83d13f3e9.png)

Man kann die Interfaces einblenden: 
 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191225-c4e1630a-d71c-4b77-99f2-e8a34ebfeca3.png)

 
Zustandssteuerung: Ein- und Ausschalten von Geräten 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191242-1e13879c-6601-4b2c-ba79-a85e1fd7ae27.png)

 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191257-64e41291-04b3-49db-982e-16e7faf81a39.png)

 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191272-bdbf6978-e692-42a4-b4ea-2691b6cab700.png)

 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191289-255a2d8b-1d5d-4c61-87c9-381593fa03be.png)

 ![grafik](https://user-images.githubusercontent.com/102586033/172191320-3498a419-e38c-4503-80c7-0b6201b36ed8.png)

 
 
Console kennenlernen 
Mit dem Befehl help bekommt man genug Infos, um die Befehle kennenzulernen. 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191357-8eb13b83-830e-4176-9a1b-4e1ab34ef964.png)

 ![grafik](https://user-images.githubusercontent.com/102586033/172191377-70c55381-35ff-46fd-94af-94970fd8e04c.png)

 
 
Statische IP bei PC1: 
 
Statische IP festlagen 
Usage: 
Ip subnetmask gateway 
Ip 192.168.23.10 255.255.255.0 192.168.23.1 
 
Danach mit dem Befehl : show ip kann man die IP anzeigen 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191410-c7f00f61-7668-49ac-a4d9-9a66eca369e4.png)

 
Es gibt keinen DNS Server für diesen PC1 und wir müssen einen konfigurieren. 
 
Können Sie ohne DNS pingen? 
Pingen können wir mit die IP-Adresse . Wenn wir die IP-Adresse nicht kennen, können wir es nicht ohne DNS tun. 
 
Befehl Usage: ip dns 192.168.23.1 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191444-f3a0fe21-f0bf-4149-8aea-e9ea04511f49.png)

 
 
Statische IP bei PC2: 
 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191459-d4a4f823-8ded-491e-9905-cbd977de630d.png)

 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191500-d78a6d7a-2afe-4e0e-ac68-622036dff158.png)

 ![grafik](https://user-images.githubusercontent.com/102586033/172191522-d7054df1-1a46-4e2c-9bd3-dbaeb74298b1.png)

 
 
Statische IP bei PC3: 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191546-6baed9d6-d9cb-495f-9dc8-8783bda787aa.png)

 ![grafik](https://user-images.githubusercontent.com/102586033/172191562-3745ae96-35a1-4f81-a134-a5f1b6cfa77e.png)

 
 
 
 
Pingen / Erreichbarkeit 
PC3 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191584-85b1e238-998c-4a7d-829a-4a119d78e9aa.png)

 
PC2 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191602-3ba49857-96ce-4bac-b253-27c9fd6f64de.png)

 
 
PC1 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191646-9e9a530d-0873-43bb-ac25-7ce89e0d0808.png)

 ![grafik](https://user-images.githubusercontent.com/102586033/172191716-a9bf6325-0e02-4580-b77f-9a067feb5290.png)

 
 
 
 
Save config 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191751-7d8afc8e-2489-4b1f-b8d2-7783f69eb5a4.png)

 
Um Projekt zu speichern, muss man herunterfahren: 
 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191765-b900f7cb-8820-4767-a9b2-eda02678f7d5.png)

 ![grafik](https://user-images.githubusercontent.com/102586033/172191812-046600de-29c1-485f-a1c0-e5110206d1f0.png)

 
 ![grafik](https://user-images.githubusercontent.com/102586033/172191874-91da337d-8268-49f8-97ea-cea5cf080f1c.png)

 ![grafik](https://user-images.githubusercontent.com/102586033/172191931-ec439905-2f0c-4974-a7b6-e88c844b50d8.png)

 
 Die Datei:
<<gns3 ping sw.gns3project>>
 
 
Packet trace mit Wireshark durchführen 
 
 ![grafik](https://user-images.githubusercontent.com/102586033/172192000-9822e850-f9ce-4868-8f3f-4e5e2ac6ed80.png)

 ![grafik](https://user-images.githubusercontent.com/102586033/172192018-3c84043f-099c-480c-a598-2c02edcdd30f.png)

 
 ![grafik](https://user-images.githubusercontent.com/102586033/172192029-7577fcb7-55ff-4c15-9106-cf58eaef5085.png)
![grafik](https://user-images.githubusercontent.com/102586033/172192043-63f194d6-535d-48a0-be84-999713c02636.png)

 ![grafik](https://user-images.githubusercontent.com/102586033/172192068-eb30e1bb-6238-4174-ac61-8628c88eafaa.png)

 
 
 
 
 
Man schicket ein Request und mitbekommt, dass es erreichbar ist "Reply" 
ARP: Adresse Resolution Protokoll spiel hier eine Rolle. 
 
Wenn wir versuchen, eine IP-Adresse anzupingen, wird gleichzeitig eine ARP-Anfrage gesendet. der Computer wird  eine ARP-Antwort erhalten. Die ARP-Tabelle Ihres Computers enthält die IP-Adresse und die MAC-Adresse des Hosts, den Sie zu erreichen versuchen. 
 
 
 
![grafik](https://user-images.githubusercontent.com/102586033/172192102-55cdd50a-f326-46b0-bd7d-b22bf71c1ef4.png)



Die Datei:

![grafik](https://user-images.githubusercontent.com/102586033/172209322-6934fc44-bced-4189-a8b8-909b9c1c01eb.png)
[labor_ping_mit_switch_exported.zip](https://github.com/hameomar/labor/files/8846185/labor_ping_mit_switch_exported.zip)

