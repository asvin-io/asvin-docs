==============
Asvin Modell
==============

In diesem Abschnitt werden wir einen kurzen Blick auf die Architektur von Asvin werfen 
und seine Komponenten kurz erklären. Einige relevante Konzepte und Schlüsselwörter werden 
ebenfalls erläutert.

    .. image:: ../images/asvinarchitecture.png
        :alt: asvin architecture
        :width: 800pt
        :align: center

Kundenplattform
###############

asvin bietet eine benutzerfreundliche Kundenplattform, um die Komplexität der Hintergrundprozesse 
zu abstrahieren, um Geräte zu registrieren, Firmware-Rollouts einzurichten und zu planen, Gruppenaktionen 
für registrierte Geräte zu definieren und Geräte auf eine Blacklist zu setzen. Die Kundenplattform zeigt 
auch Informationen zu Firmware-Updates an und liefert die aktuelle Version der Edge-Geräte.

Version controller
##################

Der Versions-Controller hält aktuelle Informationen über die verfügbare Firmware für ein bestimmtes 
Gerät oder eine Gerätegruppe auf der asvin.io-Plattform bereit. Er ist eine der Kernkomponenten der 
asvin Architektur.


Interplanetary FileSystem
#########################

Interplanetary FileSystem oder IPFS ist ein verteiltes Peer-to-Peer-Hypermedia-Protokoll, welches 
zum Speichern und Teilen von Daten in einem verteilten Dateisystem entwickelt wurde. IPFS dient als 
eine der Kernkomponenten der asvin Architektur. asvin nutzt das `IPFS <https://ipfs.io/>`_. Protokoll 
um Firmware, Updates und Patches zu speichern. 



**Content Identifier**

Der Datenaustausch auf dezentralen Plattformen wie `IPFS <https://ipfs.io/>`_ hängt von der inhaltsbasierten Adressierung 
ab, anstatt von der lokalen Adressierung, um Daten sicher zu lokalisieren und zu identifizieren. Ein 
Content Identifier (CID) ist ein selbstbeschreibender Inhaltsadressbezeichner, kryptographischer Hash, 
typischerweise SHA-256, der 32 Bytes lang ist. Der CID für eine binäre Bilddatei, die in einem IPFS Netzwerk 
gespeichert ist, könnte **QmcRD4wkPPi6dig81r5sLdrtd1gDCL4zgpEj9CfuRrGbzFsein**.



Blockchain
##########

Die asvin-Plattform nutzt die Blockchain-Technologie, um alle Transaktionen zu speichern, die 
im asvin.io-Netzwerk ausgeführt werden, einschließlich: Geräteregistrierung, Firmware-Upload, 
Geräte-Update, Firmware-Update, Benutzerregistrierung, etc. All diese Transaktionen sind mit Hashs 
verbunden und in Blöcken gespeichert, die wiederum mit einem gesicherten Hash verbunden sind. Für 
die asvin Plattform nutzen wir die `Hyperledger Fabric <https://www.hyperledger.org/use/fabric>`_  
und `Hyperledger besu <https://www.hyperledger.org/use/besu>`_ blockchains.


**Distributed Ledger**

Distributed Ledger Technology (DLT) ist ein digitales System zur Aufzeichnung der Transaktion 
von Assets, in dem die Details von bestimmten Transaktionen an mehreren Stellen aufgezeichnet 
werden. Im Gegensatz zu traditionellen Datenbanken gibt es bei Distributed Ledger keine zentrale 
Datenspeicherung oder Verwaltungsfunktion. Die oben erwähnte Blockchain ist eine Art von DLT.


**Smart Contracts**

Ein Smart Contract ist ein Computerprogramm oder ein digitales Transaktionsprotokoll, das dazu gedacht 
ist, rechtlich relevante Ereignisse und Handlungen gemäß den Bedingungen eines Vertrages oder einer 
Vereinbarung automatisch auszuführen, zu kontrollieren oder zu dokumentieren. Das Ziel eines Smart Contracts 
ist es, den Bedarf an vertrauenswürdigen Vermittlern, Schlichtung, Durchführungskosten, Betrugsverluste sowie 
die Risikominderung von schädlichen Angriffen und unbeabsichtigten Störungen zu reduzieren.

Endgeräte oder Edge Devices
###########################

Endgeräte sind Endpunkte in der asvin.io-Architektur und in einem IoT-Netzwerk, die eine bestimmte physikalische 
Aufgabe steuern, verwalten und lösen: Edge Devices schalten zum Beispiel eine smarte Waschmaschine in einem Haus 
ein, überwachen Temperatur und Luftfeuchtigkeit in einer Chemiefabrik oder einen Luftqualität in einer Stadt. 
Diese Geräte haben als Herzstück Mikrocontroller und Sensoren und mit ihrem geringen Platzbedarf sind diese Edge 
Devices leicht in abgelegenen Gebieten unter extremen Umweltbedingungen zu betreiben. Beispiele für Edge Devices 
im Industrial Internet of Things (IIoT) sind Prozessüberwachungssensoren, Smart Meter, Lora-Knoten, Rauchmelder, etc.

