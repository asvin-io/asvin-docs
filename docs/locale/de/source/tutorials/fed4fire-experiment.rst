=====================
Fed4FIRE+ Experimente
=====================

Das Tutorial demonstriert die Schritte, die zum Starten und Verwalten der Fed4FIRE+-Experimente 
für die Durchführung von Stresstests der asvin.io-Plattform erforderlich sind, indem virtuelle 
Endgeräte mit dem asvin API-Stack simuliert werden. Diese Vorgehensweise erleichtert die detaillierte 
Analyse der Skalierbarkeit und Zuverlässigkeit der Plattform.


Voraussetzungen
###############
1. `jFed Experimenter Toolkit <https://jfed.ilabt.imec.be/>`_
2. `ESpec Generator <https://github.ugent.be/jlemaes/generate-espec>`_
3. `asvin API stack image <https://github.com/Asvin-io/tutorials/tree/main/Fed4FIRE-Experiments/image>`_
4. `Grafana json file <https://github.com/Asvin-io/tutorials/tree/main/Fed4FIRE-Experiments/grafana>`_


Erste Schritte
###############

1. Start des Experiments
        
        Zum Start und zum Überwachen der Fed4FIRE+ Experimente findet das `jFed Experimenter Toolkit <https://jfed.ilabt.imec.be/>`_ 
        Anwendung. Es ist ein benutzerfreundliches Tool mit einer einfachen und selbsterklärenden Oberfläche. 
        Loggen Sie sich mit Ihrem Fed4FIRE+ Konto in das Experimenter Tool ein. Zum Erstellen und Starten der 
        Experimente kann einfach die Drag and Drop Funktion genutzt werden. Alternativ können die 
        Experiment-Spezifikationen (ESpec) erstellt und in das Toolkit hochgeladen werden. 


        .. image:: ../images/Fed4FIRE/jFed_experiment.JPG
                :width: 350pt
                :align: center

        Zur Erstellung der ESpec wird das Tool 
        `ESpec Generator Github repository <https://github.ugent.be/jlemaes/generate-espec>`_, 
        das im Github-Repository ESpec Generator verfügbar ist. Mit diesem Tool kann ESpec nur 
        für die Testbeds Virtual Wall1 und Wall2 generiert werden. Es enthält alle Installationsskripte 
        des Kubernetes-Clusters, der Influx-DB und anderer Tools, die für den Stresstest der Plattform erforderlich sind.


        .. image:: ../images/Fed4FIRE/espec_generator.JPG
                :width: 325pt
                :align: center

        Vor dem Ausführen des ESpec-Generators müssen die Python-Voraussetzungen durch Ausführen der 
        folgenden Zeile im Generatorordner installiert werden
        
        .. code-block:: python

           pip install -r requirements.txt
        
        Mit der generierten ESpec kann nun das Experiment auf Fed4FIRE+ Testbeds gestartet werden. Das 
        Experiment besteht aus einem Master-Knoten, einen influxdb-Knoten und weiteren Arbeitsknoten Wenn 
        die ESpec für 5 Knoten generiert wurde, dann besteht das Experiment aus einem Master-Knoten, einem 
        influxdb-Knoten und 5 Worker-Knoten.

        **Wenn Experimente mit mehr als 15 Knoten durchgeführt werden sollen, kontaktieren Sie bitte das Fed4FIRE+-Team, bevor Sie das Experiment starten.**


2. Einrichten des Controll-Servers
        
        Nach dem erfolgreichen Start des Experiments mit einem Kubernetes-Cluster muss der Benutzer 
        den Kontroll-Server aus dem `Experiment-webserver-Github-Repository <https://github.ugent.be/jlemaes/experiment-webserver.git>`_  
        herunterladen und auf dem Master-Knoten des Kubernetes-Clusters bereitstellen.

        Befolgen Sie die im Repository angegebenen Schritte. Anschließend ist die Website des Kontrollservers über 
        die öffentliche IPv6-Adresse des Servers erreichbar.


        .. image:: ../images/Fed4FIRE/control-server_create_image.JPG
                :width: 325pt
                :align: center

3. Bereitstellen des asvin API-Stack-Images
        
Der Beispiel-Python-Code, mit dem der API-Stack zur Simulation des Edge-Geräts ausgeführt wird, 
        wird im `asvin Github repository <https://github.com/Asvin-io/tutorials/tree/main/Fed4FIRE-Experiments/image>`_. 
        von asvin bereitgestellt. Der Benutzer muss die Anmeldeinformationen für den Blockchain-Server und IPFS-Login, 
        Benutzerschlüssel und Geräteschlüssel in der Datei "UserDetails.json" angeben.

        Das Image benötigt 2 Benutzereingaben:

        - Anzahl der auszuführenden Threads
        - Der Server (Produktion oder Staging)

        Standardmäßig startet es mit 1 Thread und verwendet Staging-Server-Details
        
        Die Dateien asvincurl.py und Dockerfile werden zusammen nach .tar.gz gezippt.

        .. code-block:: bash
        
           tar cvfz asvin_stage2.tar.gz asvincurl.py Dockerfile
        
        Der Steuerserver verfügt über eine Weboberfläche, über die der Benutzer mithilfe der erzeugten tar-Datei 
        ein Docker-Image erstellen kann, das dann in der Docker-Registry bereitgestellt wird.

4. Monitoring der Experimente
        
        In der Schnittstelle zur Experimentüberwachung kann ein neues Experiment mit einem der 
        Docker-Images aus der Docker-Registry erstellt werden.

        Beim Erstellen der Experimente sollten Sie die Laufzeitparameter für den Python-Code angeben. 
        Andernfalls wird der Code mit den Standardparametern ausgeführt. Außerdem sollten Sie die Anzahl 
        der Pods (Parallelen) angeben, die auf dem Kubernetes-Cluster ausgeführt werden sollen.


        .. image:: ../images/Fed4FIRE/control-server_new-experiment.JPG
                :width: 325pt
                :align: center

        Die Anzahl der parallelen Pods, die auf dem Cluster laufen, kann jederzeit während des 
        laufenden Experiments geändert werden.

5. Analyse der Daten in Grafana
        Das im Experiment laufende asvin API-Stack-Image speichert die folgenden Werte im influxdb-Server.
        
        1. Gesamte Anfragen an Versionskontroller, Blockchain- und IPFS-Server
        2. Gesamtzahl der erfolgreich bedienten Anfragen von Versionskontroller, Blockchain- und IPFS-Servern
        3. Summe der fehlgeschlagenen Anfragen von Versionskontroller-, Blockchain- und IPFS-Servern
        4. Antwortzeiten der einzelnen Anfragen an alle 3 Server
        5. Erfolgreiche Firmware-Updates

        In Grafana werden diese Werte vom influxdb-Server geholt und als Zeitseriendiagramme visualisiert, 
        um die Robustheit der asvin-Plattform zu analysieren. Die `Beispiel-Json-Datei <https://github.com/Asvin-io/tutorials/tree/main/Fed4FIRE-Experiments/grafana>`_ 
        kann zur Erstellung eines Grafana-Dashboards verwendet werden.



        .. image:: ../images/Fed4FIRE/Grafana.JPG
                :width: 325pt
                :align: center
                

        






    



