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

Lizenzen:

Für diese Version ist die Aktivierung nicht möglich

![grafik](https://user-images.githubusercontent.com/102586033/177214561-5db61a85-6320-4dbb-be70-c9a6bc052b4d.png)


![grafik](https://user-images.githubusercontent.com/102586033/177215689-8431019a-ff3d-4b59-8c14-df1044330300.png)


![grafik](https://user-images.githubusercontent.com/102586033/177215901-79a3b838-0c83-438c-aadc-e6859120b72a.png)


![grafik](https://user-images.githubusercontent.com/102586033/177215963-2ca49e48-5db1-4553-944b-b17c10df7613.png)


________________________

R1, R2 Konfiguration:

![grafik](https://user-images.githubusercontent.com/102586033/177217859-626a5145-9dc4-4dd7-9c27-2211246d73c8.png)


__________________________

DHCP Setup


![grafik](https://user-images.githubusercontent.com/102586033/177216754-cf8346b2-f544-4480-bebf-c6287489aedc.png)


______________
Debian Client

# Interface>

![grafik](https://user-images.githubusercontent.com/102586033/177217039-f3490c85-4a80-4366-8bef-a1efd9f82a48.png)

# Hostname>

![grafik](https://user-images.githubusercontent.com/102586033/177217109-faf917c8-b61e-414d-bfba-2d849ae30ce2.png)


# lxde Instalaltion

![grafik](https://user-images.githubusercontent.com/102586033/177217903-bc9eae5f-3b6a-4137-83ce-527f6c417ef4.png)



___________________

# Alle ausgehenden IP Pakete auf R1-ether2 werden "masqueraded" (NAPT)

Network Address Port Translation (NAPT) ist eine Technik, bei der Portnummern und private IP-Adressen (Internet Protocol) von mehreren internen Hosts auf eine öffentliche IP-Adresse abgebildet werden.

Es handelt sich dabei um eine Art von Netzwerkadressenübersetzung (NAT), die die Möglichkeiten erweitert, indem sie bei der Kommunikation mit einem externen Netzwerk neben der IP-Adresse auch Portnummern übersetzt und zuordnet

![grafik](https://user-images.githubusercontent.com/102586033/177217965-3ed27686-4a2b-42f2-8bc1-5eab681b8a0e.png)


![grafik](https://user-images.githubusercontent.com/102586033/177218157-59b96598-d41c-4a44-b876-2d15e8541e36.png)




