
 

Switch 

Ein Switch ist ein Kopplungselement, das mehrere Hosts in einem Netzwerk miteinander verbindet. In einem Ethernet-Netzwerk, das auf der Sterntopologie basiert, dient ein Switch als Verteiler für die Datenpakete. 

 

Layer 2 Switch vs Layer 3 

Der Unterschied zwischen einem Layer-2-Switch und einem Layer-3-Switch ist die Routing-Funktion. Ein Layer-2-Switch arbeitet nur mit MAC-Adressen.Ein Layer-3-Switch hingegen kann auch statisches Routing und dynamisches Routing durchführen, einschliesslich IP- und VLAN-Kommunikation (Virtual Local Area Network). 

 

Layer2 Switch 
	

Layer 3 Switch 

Dieser Switch arbeitet auf Layer 2 
	

Arbeitet auf Layer 3 

Arbeitet mit MAC Adressen 
	

Verwendet IPs und kann die Aufgabe eines Switches übernehmen  

 

 

Ping mit Switch via GNS3 

 

GNS3 wird von Netzwerkadministratoren verwendet, um virtuelle und reale Netzwerke zu emulieren, zu konfigurieren, zu testen und Fehler zu beheben. 

Mit Drag und Drop Funktionen kann man Geräten zu einem Workspace einfügen und konfigurieren, testen. 

 

Wir werden uns mit einem Remote Server verbinden, damit wir unsere Topologie zeichnen und testen können. Der Vorteil ist, dass man kein extra VMs für GNS3 braucht. 

 
ping mit swtich-l - GNS3 Eile Edit Yiew Control Node Annotate 1001s Help To I Summa Node Servers Summa Console Cloud-HF-43 CPU 0.1%, RAM 4.4%

 

Ein Swicht verfügt über Interfaces und diese werden für "Geräte-Einschließen" genutzt. 

 

 
File Edit View Control End devices Cloud Node Annotate Tools Help C To I Summa Node PCI PC2 PC3 Console telnet 192.168.23.1:5001 telnet 192.168.23.1:5003 telnet 192.168.23.1:5005 Debian 10 Minimal 10.20 Micro Core Linux 6.4 NAT vpcs PC3 vpcs Switch 1 a Ethernet0 Ethernetl Ethernet2 Ethernet3 Ethernet4 vpcs Ethernet5 Ethernet6 Ethernet7 Switchl none rvers Summa Cloud-HF-43 CPU 0.1%, RAM 4.4%

 

 

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

 

 
Unbekannter Adapter OpenVPN TAP-Windows6: Verbindungsspezifisches DNS-Suffix: Cloud-HF -43 . local Beschreibung. Physische Adresse . . . . . . . . : DHCP aktiviert. Autokonfiguration Verbindungslokale IPv4-Adresse Subnetzmaske Lease erhalten. . Lease Iäuft ab. Standardgateway DHCP-server DHCPv6-1AID DHCPv6-C1ient -DUID. aktiviert IPv6-Adresse DNS -Server NetBIOS über TCP/IP TAP-Windows Adapter V9 ØØ-FF-CB-AØ-68-4E . fe8ø: : 691a : 6aØa :95a4: . 192.168.23.13Ø(Bevorzugt) . 255.255.255.ø . Dienstag, 31. Mai 2022 . Dienstag, 31. Mai 2022 . 192.168.23.1 : 419495883 : ØØ-Ø1-ØØ-Ø1-25-D6-E9-57-64-79-FØ-CC-ØE-48 . 8.8.8.8 : Aktiviert

 

 

Und deswegen werde ich diese Netzwerk verwenden, um mein Labor zu konfigurieren. 

 
301s Help 1192.168.23.12 PC3 vpcs Swi chl PCI PC2 vpcs vpcs 192.168.23.10 1192.168.23.11

 

 
ping mit swt ile Edit View Control End devices Cloud Node Annotate 1001s Help Start/Resume all nodes _ Debian 10 Minimal 10.20 Micro Core Linux 6.4 CD NAT vpcs

 
1192.168.23.12 PC3 vpcs Swi chl PCI PC2 vpcs vpcs 192.168.23.10 1192.168.23.11

 

Man kann die Interfaces einblenden: 

 

 
File Edit View Control End devices Cloud Node Annotate Tools Help C To I Node Summa Console 1192.168.23.12 PC3 vpcs Swi c PCI PC2 PC3 telnet 192.168.23.1:5001 telnet 192.168.23.1:5003 telnet 192.168.23.1:5005 _ Debian 10 Minimal 10.20 Micro Core Linux 6.4 cro NAT vpcs PCI Ivpcs 192.168.23.10 PC2 vecs 1192.168.23.11 Switchl none Servers Summa Cloud-HF-43 CPU 2.9%, RAM 4.5%

 

Zustandssteuerung: Ein- und Ausschalten von Geräten 

 
192.168.23.12 vpcs el Configure Console Start Suspend Stop C Reload Custom console Change hostname

 
"tich-l-l-l - GNS3 /iew Control Node Annotate 1001s Help e Confirm Start All x Are you sure you want to start all devices? Yes \192.168.23.12: PC31 vpcs :e31 :Swi chl : el No I PCI vpcs : 192.168.23.10, I PC2: vpcs \192.168.23.11
mit swtich-l-l-l - GNS3 lit View Control Node x Annotate 1001s Help To I Node Summa Console 192.168.23.12 PC3 PCI PC2 PC3 telnet 192.168.23.1:5001 telnet 192.168.23.1:5003 telnet 192.168.23.1:5005 vpcs Swi el PCI vpcs 192.168.23.10 1 PC2 vpcs 192.168.23.11 Switchl none Servers Summa Cloud-HF-43 CPU 1.4%, RAM 4.6%

 

 
1192.168.23.12 vpcs 1 el PCI vpcs 192.168.23.10 vpcs 92.168.23.11

 
Swi chl el PCI vpc- Configure Console Start 192.168. Suspend Stop C Reload Custom console vpcs 1192.168.23.11

 

Console kennenlernen 

Mit dem Befehl help bekommt man genug Infos, um die Befehle kennenzulernen. 

 
PCI - PuTTY Executing the startup file PCI> help clear ARG dhcp [OPTION] disconnect echo TEXT help history ip ARG [OPTION] load [FILENAME] ping HOST [OPTION ...J quit relay ARG rlogin tip] port save set ARG show [ARG sleep [seconds] [TEXT] trace HOST [OPTION . version print help Shortcut for: show arp. Show arp table Clear IPv4/IPv6, arp/neighbor cache, comnand history Shortcut for: ip dhcp. Get IPv4 address via DHCP Exit the telnet session (daemon mode) Display TEXT in output. See also set echo ? print help Shortcut for: show history. List the comnland history Configure the current VPC's IP settings. See ip ? Load the configuration/ script from the file FILENAME ping HOST with ICMP (default) or TCP/UDP. See ping ? Quit program Configure packet relay between UDP ports. See relay ? Telnet to port on host at ip (relative to host PC) Save the configuration to the file FILENAME Set VPC name and other options. Try set ? print the information of VPCs (default) . See show ? print TEXT and pause running script for seconds print the path packets take to network HOST Shortcut for: show version To get conmand syntax help, please enter ' ? ' as an argument of the conmand. PCI>

 
ip ARG [OPTION] Configure the current VPC' s IP settings ARG . address [mask] [gateway] address [gateway] [mask] auto dhcp [OPTION] —d Set the VPC's ip, default gateway ip and network mask Default IPv4 mask is /24, IPv6 is /64. Example: ip 10.1.1.70/26 10.1.1.65 set the VPC's ip to 10.1.1.70, the gateway to 10.1.1.65, the netmask to 255.255.255.192. In tap mode, the ip of the tapx is the maximum host ID of the subnet. In the example above the tapx ip would be 10.1.1.126 mask may be written as /26, 26 or 255.255.255.192 Attempt to obtain IPv6 address, mask and gateway using SLAAC Attempt to obtain IPv4 address, mask, gateway, DNS via DHCP dns ip dns6 ipv6 domain NAME PCI> Show DHCP packet decode Renew DHCP lease Re s e DHCP s Set DNS server ip, delete if ip is 'O' Set DNS server ipv6, delete if ipv6 is Set local dornain name to NAME 'O'

 

Statische IP bei PC1: 

 

Statische IP festlagen 

Usage: 

Ip subnetmask gateway 

Ip 192.168.23.10 255.255.255.0 192.168.23.1 

 

Danach mit dem Befehl : show ip kann man die IP anzeigen 

 
PCI - PuTTY auto dhcp [OPTION] —d dns ip dns6 ipv6 domain NAME RHOST : PORT Attempt to obtain IPv6 address, Attempt to obtain IPv4 address, Show DHCP packet decode Renew DHCP lease Re s e DHCP s mask and gateway using SLAAC mask, gateway, DNS via DHCP Set DNS server ip, delete if ip is 'O' Set DNS server ipv6, delete if ipv6 is Set local domain name to NAME 'O' 192.16B. 23. 10 2±5.2ss.2ss.11 192.16B. 23.1 PCI> PCI> ip 192.16B.23.10 255.255.255.0 192.16B.23.1 Checking for duplicate address.. . PCI . 192.168.23.10 255.255.255.0 gateway 192.168.23.1 PCI> show ip IP/MASK GATEWAY DNS MAC LPORT MTU PCI [1] . 192.168.23.10/24 . 192.168. 23.1 . 20008 . 127.0.0.1:20009 . 1500

 

Es gibt keinen DNS Server für diesen PC1 und wir müssen einen konfigurieren. 

 

Können Sie ohne DNS pingen? 

Pingen können wir mit die IP-Adresse . Wenn wir die IP-Adresse nicht kennen, können wir es nicht ohne DNS tun. 

 

Befehl Usage: ip dns 192.168.23.1 

 
PCI> ip dns 192 PCI> show ip .168.23 IP/MASK GATEWAY DNS MAC LPORT RHOST : PORT MTU PCI> PCI [1] . 192.168.23.10/24 . 192.168. 23.1 . 192.168. 23.1 . 20008 . 127.0.0.1:20009 . 1500

 

 

Statische IP bei PC2: 

 

 
PC2> show ip IP/MASK GATEWAY DNS MAC LPORT RHOST : PORT MTU . 0.0.0.0/0 . o.o.o.o . 20006 . 127.0.0.1:20007 . 1500 PC2> ip 192.168.23.11 255.255.255.0 192.168.23.1 Checking for duplicate address.. . pc 2 . 192.168.23.11 255.255.255.0 gateway 192.168.23.1 PC2> ip dns 192.168.23.1

 
PC2> show IP/MASK GATEWAY DNS MAC LPORT RHOST : PORT MTU . 192.168.23.11/24 . 192.16B.23.1 . 192.168. 23.1 . 20006 . 127.0.0.1:20007 . 1500

 

 

Statische IP bei PC3: 

 
PC3> ip 192.168.23.12 255.255.255.0 192.168.23.1 Checking for duplicate address.. . pc 3 . 192.168.23.12 255.255.255.0 gateway 192.168.23 1 PC3> ip dns 192.168.23.1

 

 
PC3> show NAME IP/MASK GATEWAY DNS MAC LPORT RHOST : PORT MTU PC3[1] . 192.168.23.12/24 . 192.168. 23.1 . 192.168. 23.1 . 20010 . 127.0.0.1:20011 . 1500

 

 

Pingen / Erreichbarkeit 

PC3 

 
PC3> host PC3> PuTTY ping 192.16B.23.1 (192.168 .23.1) not reachable clear clear ipl ipv6 larplneighborlhist Clear ip/ ipv6 address, arp/neighbor table, conmand time= . o time= . 0 time= . o time= . o t ime= time= . o t ime= time= . o history. PC3> ping 192 84 bytes from 84 bytes from 84 bytes from 84 bytes from PC3> ping 192 84 bytes 84 bytes 84 bytes 84 bytes PC3> from from from from .168.23.10 192.168.23 192.168.23 192.168.23 192.168.23 .168. 192.168.23 192.168.23 192.168.23 192.168.23 .10 .10 .10 .10 .11 .11 .11 .11 1 cmp 1 cmp 1 cmp 1 cmp 1 cmp 1 cmp 1 cmp 1 cmp seq=l seq=2 seq=3 seq=4 seq=l seq=2 seq=3 seq=4 tt1=64 tt1=64 tt1=64 tt1=64 tt1=64 tt1=64 tt1=64 tt1=64 622 9 99 553 778 0.886 966 1.105 993 ms ms ms ms ms ms ms ms

 

PC2 

 
PC2 PuTTY Checking for duplicate address.. . pc 2 . 192.168.23.11 255.255.255.0 gateway 192.168.23.1 PC2> ip dns 192.168.23.1 RHOST : PORT time=0. 949 ms tt1=64 time=O. 991 ms tt1=64 time=0.891 ms tt1=64 tt1=64 time=1.014 ms tt1=64 time=O. 938 ms tt1=64 time=O. 944 ms tt1=64 tt1=64 PC2> show ip IP/MASK GATEWAY DNS MAC LPORT MTU . 192.168.23.11/24 . 192.16B.23.1 . 192.168. 23.1 . 20006 . 127.0.0.1:20007 . 1500 PC2> ping 192 84 bytes from 84 bytes from 84 bytes from 84 bytes from PC2> ping 192 84 bytes 84 bytes 84 bytes 84 bytes PC2> from from from from .168.23.10 192.168.23 192.16B.23 192.16B.23 192.168.23 .168.23.12 192.168.23 192.16B.23 192.16B.23 192.168.23 .10 .10 .10 .10 .12 .12 .12 .12 icmp seq=l icmp seq=2 icmp seq=3 icmp seq=4 icmp seq=l icmp seq=2 icmp seq=3 icmp seq=4 t ime= t ime= 1.087 ms 0.879 ms

 

PC1 

 
PuTTY RHOST : PORT tt1=64 tt1=64 tt1=64 tt1=64 tt1=64 tt1=64 tt1=64 tt1=64 MTU 1500 PCI> ip 192.168.23.10 255.255.255.0 192.168.23.1 Checking for duplicate address.. . ACPCI . 192.168.23.10 255.255.255.0 gateway 192.168.23 1 PCI> ip dns 192.168.23.1 PCI> show ip IP/MASK GATEWAY DNS MAC LPORT MTU PCI [1] . 192.168.23.10/24 . 192.168. 23.1 . 192.168. 23.1 . 20008 . 127.0.0.1:20009 . 1500 PCI> ping 192 84 bytes from 84 bytes from 84 bytes from 84 bytes from PCI> ping 192 84 bytes bytes bytes bytes from from from from .168.23.11 192.168.23 192.168.23 192.168.23 192.168.23 .168.23.12 192.168.23 192.168.23 192.168.23 192.168.23 .11 .11 .11 .11 .12 .12 .12 .12 1 cmp 1 cmp 1 cmp 1 cmp 1 cmp 1 cmp 1 cmp 1 cmp seq=l seq=2 seq=3 seq=4 seq=l seq=2 seq=3 seq=4 t ime= time= time= t ime= time= time= time= time= . o 1.084 0.974 1.111 ms 0.976 ms 0.786 ms 0.998 1.114 986 ms ms ms ms ms

 

 
e Ping mit swtich-l - GNS3 File Edit View Control Node End devices RHOST : PORT RHOST : PORT tt1=64 949 ms tt1=64 tt1=64 tt1=64 Annotate Cloud Debian 10 Minimal 10.20 Micro Core Linux 6.4 NAT vpcs - PuTTY . 1500 Tools Help C To I Node Summa Console 1192.168.23.12 PC3 vpcs Swi chl el PCI PC2 PC3 telnet 192.168.23.1:5001 telnet 192.168.23.1:5003 telnet 192.168.23.1:5005 PCI vpcs 192.168.23.10 PC2 - PuTTY Switchl none Servers Summa Cloud-HF-43 CPU 1.6%, RAM 4.5% PCI MTU PCI> ip 192.168.23.10 255.255.255 Checking for duplicate address.. . ACPCI . 192.168. 23.10 255.255.255 PCI> ip dns 192.168.23.1 .0 192.168.23 1 192.168. 23.1 ga teway Checking for duplicate address.. . PC2 . 192.168. 23.11 255.255.255 PC2> ip dns 192.168.23.1 ga teway seq=l seq=2 seq=3 seq=4 PC2 vpcs 1192.168.23.11 192.168. 23.1 time= . o t ime= t ime= t ime= PCB - PuTTY PC3> ping 192.16B.23.1 host (192.168 .23.1) not reachable PC3> clear clear ipl ipv6 larplneighborlhist PCI> show ip IP/MASK GATEWAY DNS MAC LPORT MTU PC2> show ip NAME IP/MASK GATEWAY DNS MAC L PORT MTU . 192.168.23.11/24 . 192.168. 23.1 . 192.16B.23.1 . 20006 . 127.0.0.1:20007 . 1500 Clear ip/ ipv6 address, arp/neighbor table, c 01 PCI [1] . 192.168.23.10/24 . 192.168. 23.1 . 192.168. 23.1 . 20008 . 127.0.0.1:20009 . 1500 PC3> ping 192 B4 bytes from B4 bytes from B 4 bytes from B 4 bytes from mec PC3> ping 192 PCI> ping 192 .168.23.11 192.168.23 192.168.23 192.168.23 192.168.23 .168.23.10 192.168.23 192.168.23 192.168.23 192.168.23 .168.23.12 .10 .10 .10 .10 1 cmp 1 cmp 1 cmp 1 cmp 0.991 ms 0.891 ms 1.087 bytes bytes bytes bytes from from from from .11 .11 .11 .11 ms .168.23.10 192.168.23 192.168.23 192.168.23 192.168.23 .168.23.11 192.168.23 192.168.23 192.168.23 192.168.23 .10 .10 .10 .10 .11 .11 .11 .11 1 cmp 1 cmp 1 cmp 1 cmp 1 cmp 1 cmp 1 cmp 1 cmp seq=l seq=2 seq=3 seq=4 seq=l seq=2 seq=3 seq=4 tt1=64 tt1=64 tt1=64 tt1=64 tt1=64 tt1=64 tt1=64 tt1=64 1 cmp 1 cmp 1 cmp 1 cmp seq=l seq=2 seq=3 seq=4 tt1=64 tt1=64 tt1=64 tt1=64 t ime= t ime= t ime= time= 1.084 ms 0.974 ms 1.111 ms 0.976 ms PC2> ping 192 84 bytes from 84 bytes from 84 bytes from 84 bytes from PC2> ping 192 B4 bytes B4 bytes B 4 bytes B 4 bytes PC3> from from from from

 

Save config 
ping 192 time= .886 tt1=64 time= . 966 tt1=64 34 bytes from 786 ms tt1=64 tt1=64 34 bytes from tt1=64 time= . 993 tt1=64 34 bytes from tt1=64 34 bytes from tt1=64 save .168.23.12 192.168.23 192.168.23 192.168.23 192.168.23 .12 .12 .12 .12 1 cmp 1 cmp 1 cmp 1 cmp seq=l seq=2 seq=3 seq=4 tt1=64 tt1=64 tt1=64 tt1=64 time= . o t ime= 0.998 t ime= 1.114 time= . o 986 Ipc2> ping 192 84 bytes from B4 bytes from B4 bytes from B4 bytes from PC2> save .168.23.12 192.168.23 192.168.23 192.168.23 192.168.23 .12 .12 .12 .12 1 cmp 1 cmp 1 cmp 1 cmp seq=l seq=2 seq=3 seq=4 84 84 time- -84 time- -84 time-Ac t ime bytes bytes bytes bytes save from from from from 192.168.23 192.16B.23 192.168.23 192.168.23 .11 .11 .11 .11 1 cmp 1 cmp 1 cmp 1 cmp seq=l seq=2 seq=3 seq=4 o o time= . 1 105 o ms ms ms Saving startup configuration to startup. vpc done Saving startup configuration to startup. vpc Saving startup configuration to startup. vpc

 

Um Projekt zu speichern, muss man herunterfahren: 
e Ping mit swtich-l - GNS3 Eile Edit Yiew Control Node Annotate 1001s Help End devices Cloud _ Debian 10 Minimal 10.20 Micro Core Linux 6.4 NAT vpcs Confirm Stop All x Are you sure you want to stop all devices? Yes 1192.168.23.12 PC3 vpcs Swi chl el No PCI vpcs 192.168.23.10 PC2 vpcs 1192.168.23.11

 

 

 
ping mit swtich-l-l - GNS3 File Edit View Control Node End devices Cloud x Annotate Tools Help C To I Node Summa Console 192.168.23.12 PC3 vpcs Swi chl el PC2 PC3 telnet 192.168.23.1:5008 telnet 192.168.23.1:5010 telnet 192.168.23.1:5012 _ Debian 10 Minimal 10.20 Micro Core Linux 6.4 NAT vpcs PCI vpcs 192.168.23.10 PC2 vpcs 192.168.23.11 Switchl none Servers Summa Cloud-HF-43 CPU 0.2%, RAM 4.5%

 
<<gns3 ping sw.gns3project>>

 

 

Packet trace mit Wireshark durchführen 

 
PCI vpcs Packet filters Suspend Style Delete

 
e Packet capture Link type: Ethernet File name: Switchl Ethernetl to PCI EthernetO Start the capture visualization program x

 
To The Wireshark Network Analyzer [Switchl Ethernetl to PCI Ethernet0] File Edit View Go Capture Analyze Statistics Telephony Wireless Tools Bpply a display filter <Ctrl-/> PCI VPCS 192.168.23.10 7 Ready to load or capture Help No Packets Summa x Profile: Default

 
PC2 - PuTTY PC2> PC2> ping 192 84 bytes from 84 bytes from Capturing from - [Switchl Ethernetl to PCI EthernetOl File Edit View Go Capture Analyze Statistics Telephony Apply a display filter <Ctrl-/> Wireless Tools .168.23.10 .168 .23.10 icmp seq=l tt1=64 time=O.840 ms 192 .168 .23.10 icmp seq=2 tt1=64 time=1.087 ms 192 Servers Summary' Time 1 ø.øøøøøø 2 0. 000500 3 0.000983 4 0.001401 5 1.002383 6 1.002921 Source Private Private 192. 168.23 .11 192. 168.23 .10 192. 168.23 .11 192. 168.23 .10 Destination Broadcast Private 192. 168.23 .10 192. 168.23 .11 192. 168.23 .10 192. 168.23 .11 Help Protocol ARP AR p ICMP ICMP ICMP ICMP Length Info 64 Who has 192.168.23.10? Tel 64 192.168.23.10 is at 00:50: 98 Echo 98 Echo 98 Echo 98 Echo (ping) (ping) (ping) (ping) id request reply request reply id=0x id=0x id=0x id=øx > > > Frame 1: 64 bytes on wire (512 bits), 64 bytes captured (512 bits) on interface Ethernet Il, Src: Private_66:68:Ø1 (00:50: Dst: Broadcast (ff:ff:ff:ff:ff:ff) Address Resolution Protocol (request)

 
Wireshark• Packet 1 • v Frame 1: 64 bytes on wire (512 bits), 64 bytes captured (512 bits) on interface Interface id: (-) > Encapsulation type: Ethernet (1) Arrival Time: May 31, 2022 09:37:22.7923Ø8øøø Mitteleuropäische Sommerzeit 68 01 08 06 øø 01 17 0b id [Time Epoch [Time [Time [Time Frame Frame shift for this packet: Ø.ØØØØØØØØØ seconds] Time: 1653982642.7923Ø8øøø seconds delta from previous captured frame: Ø.ØØØØØØØØØ seconds] delta from previous displayed frame: Ø.ØØØØØØØØØ seconds] since reference or first frame: Ø.ØØØØØØØØØ seconds] Number: 1 Length: 64 bytes (512 bits) Capture Length: 64 bytes (512 bits) [Frame is marked: False] [Frame is ignored: False] [Protocols in frame: eth: ethertype : arp] [Coloring [Coloring Rule Name: ARP] Rule String: arp] 0000 0010 0020 0030 50 50 66 66 08 øø 06 øø 01 øø ff 79 79 17 68 01 . p yfh . p yfh

 

Man schicket ein Request und mitbekommt, dass es erreichbar ist "Reply" 

ARP: Adresse Resolution Protokoll spiel hier eine Rolle. 

 

Wenn wir versuchen, eine IP-Adresse anzupingen, wird gleichzeitig eine ARP-Anfrage gesendet. der Computer wird  eine ARP-Antwort erhalten. Die ARP-Tabelle Ihres Computers enthält die IP-Adresse und die MAC-Adresse des Hosts, den Sie zu erreichen versuchen. 

 
Apply a display filter <Ctrl-/> Protocol Length Info tt1=64 tt1=64 tt1=64 tt1=64 AR p ARP ICMP ICMP ICMP ICMP 64 Who has 192.168.23.10? Tell 192.168.23.11 64 192.168.23.10 is at 98 Echo 98 Echo 98 Echo 98 Echo (ping) (ping) (ping) (ping) request reply request reply id=øxb2c5, id=0xb2c5 , id=0xb3c5 , id=øxb3c5, seq seq seq seq -1/256, -1/256, -2/512, -2/512, (reply in 4) (request in 3) (reply in 6) (request in 5)

 
