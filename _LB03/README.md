<img align="left" width="80" height="80" src="./img/../../img/docker-logo1.png" alt="Docker Logo">

# Docker
Docker ist eine Form von Paas (Platform as a Service) welche OS-Level virtualisierung verwendet, zur Bereitstellung sogennanter Contaier. Diese sind grundsätzlich von einander isoliert, konnen jedoch durch das öffnen von Ports und daserstellen von Netzwerken zusammengeschlossen werden. Durch den Zusammenschluss können mehrere Mikroservices zusammen einen grösseren Dienst zur Verfung zu stellen.

Mehr Informationen können unter [Docker Hub](https://hub.docker.com/) gefunden werden.

## Meine LB03
Für meine LB03 habe ich mich dazu entschieden einen Wordpress Server zu installieren, an diesen habe ich eine Datenbank angeschlossen und einen direkten Webserver, wlcher die Website von Wordpress anzeigt.

[Hier die wichtigsten Befehle](https://github.com/nickegli/Modul_300/blob/master/_LB03/documents/commands.md)

## Container erstellen
Das Dockerfile kann mit dem Befehl `docker build -t websrv-egli .` erstellt werden. Dabei wird das Dockerfile aus dem lokalen Verzeichniss genommen und für die Erstelung des Images verwendet.

## Starten der Umgebung
Meinen Container kann ich mit dem Befehl `docker run -it websrv-egli bash` aufstarten.

## Anweisungen Dockerfile
* `FROM`
  * definiert welches Image für den Container verwendet werden sollte.
* `ADD`
  * Ermöglicht das Hinzufügen externer Inhalte.
* `CMD`
  * Nach dem Aufstarten des Containers, werden die folgenden Befehle in einem CMD ausgeführt. Dabei ist jedoch wichtig, dass der `sudo` Befehl nicht verwendet wird, da man sowieso schon mit erhöhten Berechtigungen arbeitet.
* `ENV`
  * Diese Anweisung ermöglicht es Variabeln zu deffinieren, welche im weiteren Verlauf der Installation genutzt werden können.

##  Netzwerk

MySQL Container permanent an Host Port 3306 weiterleiten:

```
$ docker run --rm -d -p 3306:3306 mysql
```

MySQL Container mit nächsten freien Port verbinden:

```
$ docker run --rm -d -P mysql
```

## Monitoring
Das Monitoring meiner Umgebung habe ich mit CAdvisor von Google gelöst. Diesen Container habe ich ebenfalls in meinem Docker-compose file definiert. Dieser Service sammelt alle Daten meiner Umgebung und nimmt meine Logs auf, damit ich diese dort übersichtlich einsehen kann und ich ein konstantes Monitoring meiner Mikroservices habe.

### notifications
Die Benachrichtigungen können direkt auf dem C-Advisor eingerichtet werden, falls dies erwünscht ist. Dort werden auch Alerts angezeigt sobald ein gewisser PKI übedrschritten wird. Die aktive Benachrichtigung, sendet ein email an meine Adresse.

### config
<img align="center" width="" height="" src="https://github.com/nickegli/Modul_300/blob/master/img/cadvisor-conf2.PNG" alt="Monitoring">

## Security
Um die Sicherheit meienr Umgebung zu gewährleisten, habe ich einen Reverseproxy mit nginx eingerichtet. Diesen habe ich ebenfalls via Docker-compose file erstellt. Über diesen werden alle Dienste zur Verfügugn gestellt. Dies ermöglicht das alle Dienste über eine IP laufen und daher nur diese direkt angegriffen werden kann.

Ein weiterer Aspekt der Sicherheit, sind die Images. Dabei habe ich wenn möglich nicht die aktuellste Version genutzt sonder eine möglichst sichere und stabile. Zudem habe ich wo möglich den Quellcode angeschaut und geprüft, dass alle Inhalte mit meiner Umsetzung Sinn machen. Falls möglich habe ich ebenfalls ein eigenes Image erstellt und dafür zuerst ein Dockerfile geschrieben. Die Images sind im Ordner Images zu finden.

### Sicherheitsaspekte
1. Alle Container dieser Umgebung laufen auf einem Dedizierten Host, auf diesen kann nur lokal zugegriffen Werden über den Port:22
2. Der Zugriff auf Mysql und Wordpress ist mit einem Passwort geschützt
3. Nur der ReverseProxy ist von aussen sichtbar. Dahinter verbergen sich die weiteren Container meiner Umgebung.

### Reverse Proxy
<img align="center" width="" height="" src="https://github.com/nickegli/Modul_300/blob/master/img/reverse-conf2.PNG" alt="Security - Reverse Proxy">

### Berechtigungen
<img align="center" width="" height="" src="https://github.com/nickegli/Modul_300/blob/master/img/userdocker.PNG" alt="Berechtigungen">

## Testprotokoll
Wie für die LB02 habe ich hier ein weiteres Testprotokoll, ich habe versucht hierbei die wichtigsten Dienste zu prüfen um deren FUnktionalität sicherzustellen können.

<img align="center" width="" height="" src="https://github.com/nickegli/Modul_300/blob/master/img/testprotokoll3.PNG" alt="Testprotokoll">

[Go back to main Document](https://github.com/Daddey69/Modul_300/blob/master/README.md)