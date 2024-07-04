asvin’s Kundenplattform Plattform
=========================

Die asvin IoT Plattform bietet sichere OTA Updates für IoT Geräte. Folgen Sie folgenden Schritten, 
um die Plattform nutzen zu können. 

1.  *Registrierung von Devices/ Geräten*:
        
        Wenn Sie anfangen und einen Code und auf eines der unterstützten Boards in der 
        :doc:`../tutorials/tutorials` Sektion laden, beginnt das Board mit der Ausführung und ruft die definierten 
        API Routen auf. Um das Gerät zu registrieren, wird die :ref:`Register Device` API aufgerufen. 
        Nachdem diese API erfolgreich aufgerufen wurde, erscheint dein Gerät in der Untersektion 
        **"Lobby"** im Bereich **"Devices"** der Plattform.

        .. image:: ../images/register_edited.png
            :width: 400pt
            :align: center


2.  *Gerätegruppen*:
        
        Die IoT-Plattform von asvin bietet die Möglichkeit Updates für Gruppen von Geräten auszuführen. 
        Geräte können anhand verschiedener Kategorien wie Standort, Kunde, Einsatz etc. in Gruppen zusammengefasst werden. 
        So ordnen Sie ein Gerät einer Gerätegruppe zu: 

        - Erstellen Sie unter *Geräte > Gerätegruppe* > *Neue Gerätegruppe* eine neue Gerätegruppe. 
        - Navigieren Sie zu den neu registrierten Geräten zurück und fügen Sie das Gerät einer Gerätegruppe zu.


        .. raw:: html

          <video width="600" autoplay muted>
          <source src="../_static/videos/rollout.m4v" type="video/mp4">
          Your browser does not support the video tag.
          </video>

3.  *Dateigruppen*:
        
Sobald ein Gerät einer Gerätegruppe zugewiesen ist, kann ein OTA-Update hochgeladen werden. In aller Regel 
        handelt es sich dabei um eine Datei im Format *<new_firmware_file_name>.bin* oder der Dateityp, der mit dem 
        jeweiligen Geräten verbunden ist. Im Folgenden wird exemplarisch das Hochladen der Datei esp-ota-blink.bin 
        in die Dateigruppe ESP_OTA_Test gezeigt: 

    
        .. image:: ../images/upload_file.png
            :width: 400pt
            :align: center

4.  *Rollout*:
        -   In diesem Beispiel wird ein Rollout eingerichtet, um ein OTA-Update der oben angegebenen Datei an unser 
            ESP8266-Zielgerät zu übertragen. Im Abschnitt "Rollout" beginnen wir mit der Erstellung eines Rollouts. 
            Füllen Sie die Optionen wie im Screenshot gezeigt aus. Für die Priorisierung des Updates wählen Sie bitte 
            entweder Batch oder Immediately. Weiterhin besteht die Möglichkeit den Zeitpunkt für das Update zu wählen. 
            Zum Schluss wählen Sie die gewünschte Datei aus und klicken auf *Speichern*.  

            .. image:: ../images/rollout_edited.png
                :width: 400pt
                :align: center

        -   Das Rollout ist nun aktiviert. Das nächste Mal, wenn das gewählte Gerät die :ref:`Next Rollout` API, 
            anfordert und ein aktives Rollout bereitsteht, werden weitere APIs vom Gerät angefordert. 
            Das Gerät vollzieht das Update selbstständig. 
            
        -   Sobald der Rollout abgeschlossen ist, wird die neue Datei auf dem Zielgerät angezeigt. 
            In diesem Beispiel haben wir eine Blink-LED-Datei ausgerollt. Das Zielgerät ruft die 
            :ref:`Rollout Success` API auf, die in diesem Beispiel der Teil der Datei ist, den wir zuvor hochgeladen haben

        -   Die Änderung der Firmware-Version des Geräts wird auch auf der `asvin platform <https://app.asvin.io/>`_ aktualisiert
