===========
Blockchain
===========

In diesem Abschnitt werden wir die **Blockchain** -Komponente der asvin Architektur erläutern. 

    .. image:: ../images/asvinarchitecture-bc.png
        :width: 800pt
        :align: center

Blockchain ist eine Art Distributed Ledger Technology (DLT), die eine wachsende Liste von Einträgen enthält, 
die als **Blöcke** bezeichnet werden. Jeder Block enthält den `kryptographischen Hash  
<https://en.wikipedia.org/wiki/Cryptographic_hash_function>`_ des vorherigen Blocks. Durch ihr Design sind 
Blockchains beständig gegen Veränderungen der gespeicherten Daten.

In der asvin Architektur ist das Blockchain-Netzwerk auf Basis von `Hyperledger Fabric <https://www.hyperledger.org/use/fabric>`_ 
und `Hyperledger besu <https://www.hyperledger.org/use/besu>`_ aufgebaut. Kunden können wählen, welche der beiden Blockchains 
sie für ihre Einsätze nutzen möchten. Diese Blockchain-Netzwerke stellen ein Ledger zur Verfügung, das alle Transaktionen 
speichert, die im asvin.io Netzwerk ausgeführt werden, z.B.: Geräteregistrierung, Firmware-Upload, Geräte-Update, 
Firmware-Update und Benutzerregistrierung. Jede dieser Transaktionen ist mit eindeutigen Hashes gepaart und wird in 
Blöcken gespeichert, die wiederum mit einem gesicherten Hash verbunden sind. Dieser Prozess bietet Sicherheit und 
Unveränderlichkeit für den Ledger. Die asvin.io Plattform auf eine unbegrenzte Skalierbarkeit mit einem Cluster von 
Servern ausgelegt, die Fabric & Besu Netzwerke betreiben, um die Anforderungen zu verwalten um so die Funktionalität 
für Millionen von IoT-Geräten aufrecht zu erhalten.


Hyperledger Fabric
##################

Die steckbaren Module des Fabric-Netzwerks erlauben der asvin.io-Infrastruktur maximale Flexibilität, 
sodass asvin.io maßgeschneiderte Lösungen für seine IoT-Kunden entwickeln kann. Der Cluster wird mit 
`Docker swarm <https://www.docker.com/>`_. entwickelt.

**Die Fabric hat folgende Module und Dienste:**
1.	Peer: 
	eine Entität im Fabric-Netzwerk, die Anfragen von Anwendungen empfängt, einen Chaincode 	ausführt, Transaktionen validiert und den Ledger verwaltet.
2.	Orderer: 
	Dieser Dienst ordnet alle Transaktionen, die im Fabric-Netzwerk stattfinden, und leitet sie an 	die Peers weiter, um sie zu validieren.
3. MSP: 
	stellt jedem Mitglied des Fabric Netzwerks digitale Identitäten zur Verfügung.
4. Storage:
 	Das Fabric-Netzwerk nutzt CouchDB, um den aktuellen Stand der Ledger-Daten zu speichern.



Hyperledger Besu
################

Hyperledger Besu ist ein Open Source Ethereum Client. Er kann auf dem öffentlichen Ethereum-Netzwerk 
oder auf privaten, zugelassenen Netzwerken betrieben werden.

**Hyperledger Besu's Features**

1.	Die Ethereum Virtual Machine (EVM) ist eine vollständige virtuelle Turing-Maschine, die das 
   Deployment und die Ausführung von Smart Contracts über Transaktionen innerhalb einer Ethereum-Blockchain ermöglicht.
2.	Konsens-Algorithmen sind an der Validierung von Transaktionen, der Validierung von Blöcken und 
   der Produktion von Blöcken (d.h. dem Mining in Proof of Work) beteiligt.
3.	Zur Speicherung wird die Key-Value-Datenbank RocksDB verwendet, um die Daten der Kette lokal 
   zu persistieren.
4.	P2P Networking über Ethereums devp2p Netzwerkprotokolle für die Kommunikation zwischen den Clients 
   und ein zusätzliches Unterprotokoll für IBFT2.
5.	Benutzerfreundliches Mainnet Ethereum und EEA JSON-RPC APIs über HTTP und WebSocket Protokolle sowie eine GraphQL API.
6.	Die Node Performance wird mit Prometheus oder der debug_metrics JSON-RPC API Methode überwacht. 
   Die Netzwerk-Performance wird mit Alethio-Tools wie dem Block Explorer und EthStats Network Monitor überwacht.
7.	Privacy in Hyperledger Besu bezieht sich auf die Fähigkeit, Transaktionen privat zwischen den beteiligten 
   Parteien zu halten. Andere Parteien können nicht auf den Inhalt der Transaktion, die sendende Partei oder die 
   Liste der beteiligten Parteien zugreifen. Besu verwendet einen Private Transaction Manager, um Privatsphäre zu implementieren.
8.	Ein berechtigtes Netzwerk erlaubt nur bestimmten Knoten und Accounts die Teilnahme, indem es Node 
   Permissioning und/oder Account Permissioning im Netzwerk aktiviert.

Die Virtualisierung auf Betriebssystemebene wird auf dem Blockchain-Server mit Docker erreicht. 
Jeder Dienst im Netzwerk läuft in einem separaten Docker-Container und diese Container werden auf 
mehreren Maschinen des Clusters gehostet. Die Kommunikation zwischen den Containern wird mit Docker 
Swarm erreicht. Das gesamte Blockchain-Netzwerk wird mit der Docker Swarm Technologie entwickelt und betrieben.
