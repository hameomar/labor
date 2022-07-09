
# Labor 6 

 Korrektur gemäß den Anweisungen des Lehrers (DHCP ohne DHCP-Relay, mit 2 DHCP-Servern, wobei jeder Server seinen eigenen IP-Pool hat)
 
DHCP Adress Pool: Ein Netzwerkprotokoll, das es einem Server ermöglicht, einem IP-fähigen Gerät automatisch eine IP-Adresse aus einem definierten Bereich von Nummern zuzuweisen, die für ein bestimmtes Netzwerk konfiguriert sind.

# Lehrer Kommentare

1-Bei einem Router ist die Routing Tabelle die wichtigste Element, was man ganz korrekt konfigurierem muss

2-Wir haben im M123 "Server Dienste in Betrib nehmen" gelernt, dass wenn wir 2 DHCP Servern haben, müssen wir einen als Master festlegen.

* 
 Wenn Sie DHCP in einem Netzwerk mit mehreren Segmenten verwenden möchten, müssen Sie entweder einen DHCP-Server oder einen Relay-Agenten in jedem Segment einsetzen oder sicherstellen, dass Ihr Router Bootstrap Protocol (BOOTP) Broadcasts weiterleiten kann. Das Problem mit einem DHCP-Relay besteht darin, dass die Cleints keine IP erhalten, wenn beispielsweise ein Netzwerk auf dem Weg zum Zielnetzwerk ausgefallen ist. In diesem Labor werde ich daher R2 mit R3 verbinden, und wenn ein Netzwerk 172.16.28.0/30 oder 172.16.28.4/30 ausgefallen ist, wird der andere Router die IP-Zuweisung übernehmen.
 
 
 
