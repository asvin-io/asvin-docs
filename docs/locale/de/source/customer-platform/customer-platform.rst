=========================
Beehive - Plattform
=========================

In diesem Abschnitt erläutern wir die **Plattform beehive** als Bestandteil der asvin Architektur. 

    .. image:: ../images/asvinarchitecture-customerplatform.png
        :width: 800pt
        :align: center

Wir bei asvin glauben an eine einfache und benutzerfreundliche Lösung. Die asvin.io Kundenplattform bietet 
eine Abstraktionsschicht, um die Vielschichtigkeit und die Komplexität der Distributed Ledger Technologie zu 
verbergen. Diese Abstraktion wird durch einen Cluster von Servern ermöglicht, der von einem Cluster an Servern 
unterstützt wird. Ein Load Balancer sorgt dafür, dass die Menge an IoT-Geräten, die auf der asvin.io-Plattform 
verwaltet werden und, dass es keine Latenz in der Verbindung zwischen dem Netzwerk des Kunden und seinen 
IoT-Edge-Geräten und dem asvin.io-Server gibt.


**Beehive** - Die Kundenplattform beinhaltet folgende Funktionen:

1. Service Dashboard
    Es dient als Portal für die IoT-Gerätebetreiber, um direkt zu interagieren und den Update- 	und  	Patch-Status 
    ihrer Edge-Geräte zu kontrollieren. Das Portal steuert die Funktionen zum 	Hochladen von Firmware, Löschen von 
    Firmware, Verwalten von Edge-Geräten, Überprüfen 	der Gesundheitsstatistiken von Edge-Geräten und vieles weitere. 

2. Upload Firmware
    Lädt die vom Kunden bereitgestellte Firmware auf den IPFS Server hoch

3. Update Ledger
    Interagiert mit dem Hyperledger-Blockchain-Server, um die Firmware-Datenbank zu aktualisieren.

4. Update Version Control Server
    Hält den Versionskontrollserver mit Informationen über die neueste Firmware auf dem aktuellen Stand.