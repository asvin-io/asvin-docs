=========================
Interplanetary FileSystem 
=========================

In diesem Abschnitt wird das **Interplanetary FileSystem (IPFS)** als Komponente der asvin Architektur 
kurz vorgestellt und erklärt.

    .. image:: ../images/asvinarchitecture-ipfs.png
        :width: 800pt
        :align: center

asvin.io nutzt das Interplanetary File System Protokoll, um Firmware und Patches zu speichern. 
IPFS ist eine inhaltsadressierbare Peer-to-Peer-Methode (P2P) zum Speichern und Teilen von Hypermedia 
in einem verteilten Dateisystem, wobei doppelte Dateien und Redundanz vermieden werden. Es nutzt eine 
Netzwerkinfrastruktur, welche es asvin.io ermöglicht, unveränderliche Firmwaredaten zu speichern. Wenn 
eine Firmware-Datei im Netzwerk gespeichert wird, wird ein Hash basierend auf dem Inhalt der Firmware 
generiert und im Blockchain-Netzwerk gespeichert. Später wird derselbe Hash von Edge-Geräten verwendet, 
um die Firmware aus dem Datenspeicher zu extrahieren. Dies bildet einen verallgemeinerten Merkle gerichteten 
azyklischen Graphen (DAG). Jeder Knoten des Merkle DAG ist mit einem gesicherten Hash verbunden. Wenn ein 
Knoten im DAG hinzugefügt wird, wird sein Hash basierend auf dem Hash seines lokalen Inhalts und den Hashes 
der Namen seiner Unterknoten berechnet, anstatt deren Inhalt. Sobald er erstellt wurde, ist es unmöglich, 
einen Knoten im Netzwerk zu verändern. IPFS hat keinen Single Point of Failure. asvin.io bietet ein verteiltes 
Content-Delivery-System, welches eine zusätzliche Sicherheitsebene bietet und DDoS-Attacken verhindert. 
asvin.io's SDK, das auf Edge-Devices ausgeführt wird, ermöglicht es, mit Datenspeichern zu interagieren. 
Sobald ein Edge-Device vom Versions-Controller Informationen über die neu verfügbare Firmware erhält, nutzt es 
diese Informationen, um die entsprechende Firmware aus dem verteilten CDN herunterzuladen.