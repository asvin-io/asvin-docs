===========================
Endgeräte oder Edge Devices
===========================

Es folgt eine kurze Erklärung der Funktion **Edge Devices** innerhalb der asvin Architektur.

    .. image:: ../images/asvinarchitecture-edgedevice.png
        :width: 800pt
        :align: center

Die Edge Devices sind Endpunkte in der asvin.io-Architektur und haben in einem IoT-Netzwerk die Aufgabe, 
eine physikalische Aufgabe zu steuern, zu verwalten und zu lösen. In der Regel sollen Edge-Device einen 
kleinen Footprint haben und müssen in abgelegenen Gebieten unter oft extremen Umweltbedingungen einfach 
zu verwalten sein. Zum Beispiel: industrielle Prozessüberwachungssensoren, Smart Meter, Lora-Knoten etc. 
asvin stellt Bibliotheken für eine Vielzahl von Edge-Geräten zur Verfügung, um die technischen Anforderungen 
zu erleichtern, die notwendig sind, um sicher und effizient mit der asvin.io-Infrastruktur zu interagieren. 
Die asvin Bibliotheken fungieren als Schnittstelle zwischen den Edge Devices und der asvin.io Plattform. 
Das asvin.io SDK ermöglicht die einfache Nutzung von APIs zur Interaktion mit der asvin.io Update-Infrastruktur. 
Die SDKs sind anwenderfreundlich und ermöglichen es neuen IoT-Geräten, sich schnell mit der asvin.io-Infrastruktur 
zu verbinden, um direkt von einem einsatzbereiten Update-Verteilungsnetzwerk zu profitieren. Das Hauptmerkmal 
des asvin SDKs ist, dass es sich um eine generische Lösung handelt und nicht auf eine bestimmte Hardwareplattform 
wie z.B. Arduino, ESP, STM, Arm Cortex-M3, M4 etc. und Softwareprotokolle beschränkt ist.



**The asvin.io libraries installed on edge device provides following functionalities:**

1. **Device Update Management**
    - Securely register devices on asvin.io platform
2. **Check for Firmware Updates**
    - Regularly poll for updates in configurable time intervals
3. **Download and Install Firmware**
    - Download and store updated versions of firmware
    - Install the firmware based on traffic and availability of edge device
4. **Collect Health Statistics**
    - Send timely health updates of edge device on asvin.io platform e.g. firmware version in use
    - asvin.io platform generates insights from the data which can be used to extend life cycle of IoT devices and for preventive maintenance.

**Funktionen der auf dem Edge Device installierten asvin.io Bibliotheken:**

    1.	**Device Update Management**
        - Sichere Registrierung von Geräten auf der asvin.io Plattform
    2.	**Prüfen auf Firmware Updates** 
        - Regelmäßige Abfrage nach Updates in konfigurierbaren Zeitintervallen
    3.	**Herunterladen und Installieren von Firmware** 
        - Herunterladen und Speichern von aktualisierten Versionen der Firmware
        - Installiert die Firmware basierend auf dem Traffic und der Verfügbarkeit des Edge Devices. 
    4.	**Erfassen von Health Statistics** 
        - Sendet zeitnahe Health Statistics des Edge Devices an die asvin.io Plattform, z.B. die verwendete Firmware Version
        - Die asvin.io Plattform generiert Erkenntnisse aus den Daten, die zur Verlängerung des Lebenszyklus von IoT-Geräten und zur vorbeugenden Wartung genutzt werden können.
    