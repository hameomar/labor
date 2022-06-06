 
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
 
 
 
Ein Swicht verfügt über Interfaces und diese werden für "Geräte-Einschließen" genutzt. 
 
 
 
 
 
Auswahl eines Netzwerk: 
Wir haben bei diesem Labor 3 Geräten zu verbinden. Obwohl wir keinen Router in diesem Topologie haben, werde ich 2 Adressen für die Broadcast und Netzwerk ID berechenen. Das heisst wir brauchen 3 Bits. Mit 3 Bits bekommen wir 8 Adressen: 
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
 
 
 
 
 
Und deswegen werde ich diese Netzwerk verwenden, um mein Labor zu konfigurieren. 
 
 
 
 
 
 
 
 
Man kann die Interfaces einblenden: 
 
 
 
 
Zustandssteuerung: Ein- und Ausschalten von Geräten 
 
 
 
 
 
 
 
 
 
 
 
Console kennenlernen 
Mit dem Befehl help bekommt man genug Infos, um die Befehle kennenzulernen. 
 
 
 
 
 
Statische IP bei PC1: 
 
Statische IP festlagen 
Usage: 
Ip subnetmask gateway 
Ip 192.168.23.10 255.255.255.0 192.168.23.1 
 
Danach mit dem Befehl : show ip kann man die IP anzeigen 
 
 
 
Es gibt keinen DNS Server für diesen PC1 und wir müssen einen konfigurieren. 
 
Können Sie ohne DNS pingen? 
Pingen können wir mit die IP-Adresse . Wenn wir die IP-Adresse nicht kennen, können wir es nicht ohne DNS tun. 
 
Befehl Usage: ip dns 192.168.23.1 
 
 
 
 
Statische IP bei PC2: 
 
 
 
 
 
 
 
 
Statische IP bei PC3: 
 
 
 
 
 
 
 
Pingen / Erreichbarkeit 
PC3 
 
 
 
PC2 
 
 
 
PC1 
 
 
 
 
 
 
Save config 
 
 
Um Projekt zu speichern, muss man herunterfahren: 
 
 
 
 
 
 
 
<<gns3 ping sw.gns3project>>
 
 
Packet trace mit Wireshark durchführen 
 
 
 
 
 
 
 
 
 
 
 
Man schicket ein Request und mitbekommt, dass es erreichbar ist "Reply" 
ARP: Adresse Resolution Protokoll spiel hier eine Rolle. 
 
Wenn wir versuchen, eine IP-Adresse anzupingen, wird gleichzeitig eine ARP-Anfrage gesendet. der Computer wird  eine ARP-Antwort erhalten. Die ARP-Tabelle Ihres Computers enthält die IP-Adresse und die MAC-Adresse des Hosts, den Sie zu erreichen versuchen. 
 
 
 

