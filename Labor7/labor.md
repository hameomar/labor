# Labor 7

______________

# Anforderungen:

Alle Subnetze sind klar vermerkt und Abgrenzungen grafisch erkennbar

Auf PC1 ist lxde installiert

Surfen im Internet (mit Webbrowser) ist möglich.

Alle ausgehenden IP Pakete auf R1-ether2 werden "masqueraded" (NAPT)

Trial Lizenzen auf R1 und R2 sind aktiviert (MikroTik Account benötigt)

Netz A: Beliebiges IPv4 Subnet

Netz B: 192.168.X.0/24

( NET B : 192.168.50.0/24     | NET A : 192.168.100.0/24 )


X = 32 + Position in Klassenliste

# Variation (benötigt keinen MikroTik Account):

Als R1 OPNsense oder pfSense einsetzen

Als R2 cisco Router einsetzen

Windows PC ist optional
___________________________

HDD Resize:

![grafik](https://user-images.githubusercontent.com/102586033/177213081-56c5477d-5a74-4096-b176-335f77e77a44.png)


Zeichnen
![grafik](https://user-images.githubusercontent.com/102586033/177213647-961c8e55-15c2-4568-9955-25a324310a08.png)

____________________________
Wichtige Hinweise:

Eine Routing-Tabelle ist eine Reihe von Regeln, die oft in Tabellenform angezeigt werden und mit deren Hilfe bestimmt wird, wohin Datenpakete, die über ein Internet-Protokoll (IP)-Netz laufen, geleitet werden. Alle IP-fähigen Geräte, einschließlich Router und Switches, verwenden Routing-Tabellen. Siehe unten eine Routing-Tabelle:

mit der Routing Tabelle fangt man mit :

1-Default Route
2-sämtliche Netzwerke



___________________


# Lizenzen:

Für diese Version ist die Aktivierung nicht möglich

![grafik](https://user-images.githubusercontent.com/102586033/177214561-5db61a85-6320-4dbb-be70-c9a6bc052b4d.png)


![grafik](https://user-images.githubusercontent.com/102586033/177215689-8431019a-ff3d-4b59-8c14-df1044330300.png)


![grafik](https://user-images.githubusercontent.com/102586033/177215901-79a3b838-0c83-438c-aadc-e6859120b72a.png)


![grafik](https://user-images.githubusercontent.com/102586033/177215963-2ca49e48-5db1-4553-944b-b17c10df7613.png)


![grafik](https://user-images.githubusercontent.com/102586033/177254753-87854e7c-fbaa-4191-8959-0bb7ac346357.png)

Die Lizenz ist free

![grafik](https://user-images.githubusercontent.com/102586033/177267507-b9b1aadc-2291-4f6a-83df-8861e7050df7.png)

![grafik](https://user-images.githubusercontent.com/102586033/177267590-0d299d44-7e27-4742-b6c3-9f409f5c9419.png)

________________________

# R1, R2 Konfiguration:

![grafik](https://user-images.githubusercontent.com/102586033/177217859-626a5145-9dc4-4dd7-9c27-2211246d73c8.png)


__________________________

# DHCP Setup


![grafik](https://user-images.githubusercontent.com/102586033/177216754-cf8346b2-f544-4480-bebf-c6287489aedc.png)


Installation

Es gibt verschiedene DHCP-Client-Pakete. Das Standardpaket für Debian scheint dhcp-client zu sein. Es ist wahrscheinlich bereits installiert, wie Sie mit aptitude überprüfen können. Aber um sicher zu gehen, können Sie als root ausführen

aptitude install dhcp-client

Konfiguration

Grundlegende Konfiguration

Für eine Grundkonfiguration müssen Sie die Datei /etc/network/interfaces bearbeiten, in der die Schnittstellen Ihres Computers definiert sind. Wenn Sie eth0 als Schnittstelle verwenden wollen, die beim Booten über DHCP konfiguriert werden soll, fügen Sie den eth0-Eintrag hinzu

auto ens3

iface ens3 inet dhcp

Die verschiedenen Schlüsselwörter haben die folgende Bedeutung:

auto: die Schnittstelle soll während des Bootvorgangs konfiguriert werden.

inet: Die Schnittstelle verwendet TCP/IP-Netzwerke.

dhcp: Die Schnittstelle kann über DHCP konfiguriert werden.

Das ist alles.

Um das System so zu ändern, dass es eine statische IP-Adresse verwendet (nicht dhcp), ändern Sie die Datei /etc/network/interfaces wie folgt:

iface ens3 inet static

Adresse 192.168.50.2

Netzmaske 255.255.255.0

gateway 192.168.50.1


______________
# Debian Client

# Interface

![grafik](https://user-images.githubusercontent.com/102586033/177217039-f3490c85-4a80-4366-8bef-a1efd9f82a48.png)

# Hostname

![grafik](https://user-images.githubusercontent.com/102586033/177217109-faf917c8-b61e-414d-bfba-2d849ae30ce2.png)


# lxde Instalaltion

![grafik](https://user-images.githubusercontent.com/102586033/177217903-bc9eae5f-3b6a-4137-83ce-527f6c417ef4.png)


![grafik](https://user-images.githubusercontent.com/102586033/177222830-c22aafdd-bb47-4e2c-9715-9f86e70b759b.png)

___________________

# Alle ausgehenden IP Pakete auf R1-ether2 werden "masqueraded" (NAPT)

Network Address Port Translation (NAPT) ist eine Technik, bei der Portnummern und private IP-Adressen (Internet Protocol) von mehreren internen Hosts auf eine öffentliche IP-Adresse abgebildet werden.

Es handelt sich dabei um eine Art von Netzwerkadressenübersetzung (NAT), die die Möglichkeiten erweitert, indem sie bei der Kommunikation mit einem externen Netzwerk neben der IP-Adresse auch Portnummern übersetzt und zuordnet

![grafik](https://user-images.githubusercontent.com/102586033/177217965-3ed27686-4a2b-42f2-8bc1-5eab681b8a0e.png)


![grafik](https://user-images.githubusercontent.com/102586033/177218157-59b96598-d41c-4a44-b876-2d15e8541e36.png)



___________________
# Webbrowser

![grafik](https://user-images.githubusercontent.com/102586033/177252870-b8d0a5a6-aca4-47ed-b1c3-194110e26e94.png)




