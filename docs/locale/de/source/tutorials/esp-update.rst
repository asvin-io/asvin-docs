========================================================
Over the air updates mit ESP8266 (nodemcu) boards
========================================================

In diesem Tutorial sehen wir die Demonstration von OTA-Updates unter Verwendung der 
asvin IoT-Plattform und des nodemscu-Boards basierend auf dem ESP8266-Chipsatz.

    .. image:: ../images/OTA_wb.jpg
        :width: 400pt
        :align: center

Anforderungen
#############

1. nodemcu esp8266-Platine
2. Micro USB Kable
3. asvin platform Zugang 
4. PlatformIO VScode extension


Erste Schritte
##############

Gehen Sie als als erstes zum  `Github repository <https://github.com/asvin-io/asvin-tutorials>`_ von asvin 
und klonen Sie es. Der Code ist unter PlatformIO geschrieben. Importieren Sie das Projekt mit der 
PlatformIO-Erweiterung von VScode.


1.  Um fortzufahren, müssen Sie einige der Parameter im Code bearbeiten

    - Öffnen Sie die Datei main.cpp im Editor und fügen Sie die Zugangsdaten für Ihr Gerät hinzu.

        .. image:: ../images/keys_edited.jpg
           :width: 400pt
           :align: center
            
    - Geräte- und Kundenschlüssel: Diese finden Sie auf der asvin-Plattform unter der Registerkarte 
      "Einstellungen". Diese Schlüssel werden verwendet, um ein Auth-Token zu generieren.  


2.  Nach diesem Schritt erstellen Sie den Code für Arduino oder PlatformIO und laden ihn auf das ESP8266-Board hoch

3.  Dieser Sketch verwendet die populäre `WifiManager-Bibliothek <https://github.com/tzapu/WiFiManager>`_ , 
    um die WiFi-Berechtigungsnachweise zu verwalten. Nach dem Booten wird der ESP8266 einen WiFi-Hotspot mit 
    dem Namen "AutoConectAP" starten. Der Benutzer sollte sich mit seinem Handy/Laptop mit diesem verbinden 
    und seine Zugangsdaten eingeben. Diese Zugangsdaten werden im Flash-Speicher des ESP als Standard gespeichert. 
    Diese Zugangsdaten können später geändert werden.


4. **OTA einrichten**

    Die asvin IoT Plattform bietet sichere OTA Updates für IoT Geräte. Folgend wird gezeigt, 
    wie Updates eingerichtet werden können.

    1.  *Gerät registrieren*:
        
        Wenn sie den Sketch starten und auf das ESP8266 Board hochläden, beginnt das Board mit 
        der Ausführung und ruft die definierten API Routen auf. Die erste API, die es aufruft, 
        ist :ref:`Register Device`, Nachdem diese API erfolgreich aufgerufen wurde, finden Sie ihr Gerät 
        auf der Plattform unter Geräte>Just registered Devices. 

        .. image:: ../images/register_edited.png
            :width: 400pt
            :align: center


    2.  *Gerätegruppen*:
        
        asvin's IoT Plattform bietet Updates für eine Gruppe von Geräten. Das ESP Gerät kann zu 
        dieser Gruppe hinzufügt werden. Gehen Sie hierzu auf Geräte>Gerätegruppe auf *Neue Gerätegruppe*. 
        Anschließend navigieren Sie zurück zu *Lobby*, klicken auf Geräte gruppieren 
        und fügen das Gerät zurneu erstellten Gerätegruppe hinzu.
    
    3.  *Dateigruppen*:
   
        Sobald das Gerät einer Dateigruppe zugewiesen ist, kann die Datei hochgeladen werden, 
        die wir als OTA-Update zur Verfügung stellen wollen. Normalerweise handelt  es sich um 
        eine Datei mit dem Namen *<Dateiname>.bin*. In diesem Beispiel wird die Datei esp-ota-blink.bin 
        in die Dateigruppe ESP_OTA_Test hochgeladen.


        .. image:: ../images/upload_file.png
            :width: 400pt
            :align: center

    4.  *Rollout*:
        
        In diesem Schritt werden wir einen Rollout einrichten, um ein OTA-Update der oben angegebenen 
        Datei an unser ESP8266-Gerät zu liefern. In der Rollout Sektion beginnen wir mit der Erstellung 
        eines Rollouts. Fülle die Optionen wie im Screenshot gezeigt aus. Wähle entweder Batch oder 
        sofortiges Update. Es gibt eine Option, eine Zeit zu wählen oder ein Update sofort durchzuführen. 
        Wähle die Datei aus, die als Update ausgerollt werden soll und klicke auf *Speichern*.

        .. image:: ../images/rollout_edited.png
            :width: 400pt
            :align: center

    5.  Das Rollout ist nun aktiviert. Wenn das Gerät das nächste Mal die :ref:`Next Rollout` API abfragt, 
        wird der Rollout verfügbar sein und weitere APIs werden im ESP-Gerät aufgerufen. Das ESP-Gerät 
        wird sich danach mit der Datei aktualisieren, die wir zuvor hochgeladen haben. In diesem Fall 
        werden wir die LED auf unserem ESP-Board blinken sehen.

    6.  Sobald der Rollout abgeschlossen ist, wird die neue Datei auf dem Board ausgeführt. 
        In diesem Fall haben wir eine Blink-LED-Datei ausgerollt. Das Board wird die :ref:`Rollout Success`
        API aufrufen, die Teil der Datei esp-ota-blink.bin ist, die wir zuvor hochgeladen haben.

    7.  Die Änderung der Firmware-Version des Geräts wird auch auf der 
        `asvin platform <https://app.asvin.io/>`_ aktualisiert.
         

Damit haben wir den OTA-Rollout erfolgreich abgeschlossen. Den vollständigen Code und die Dateien 
finden Sie in asvins `Github repository <https://github.com/Asvin-io/tutorials>`_  . 