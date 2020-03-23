<img align="left" width="80" height="80" src="./img/../../img/docker-logo1.png" alt="Docker Logo">

# Container / Docker
Docker ist eine Form von Paas (Platform as a Service) welche OS-Level virtualisierung verwendet, zur Bereitstellung sogennanter Contaier. Diese sind grundsätzlich von einander isoliert, konnen jedoch durch das öffnen von Ports und daserstellen von Netzwerken zusammengeschlossen werden. Durch den Zusammenschluss können mehrere Mikroservices zusammen einen grösseren Dienst zur Verfung zu stellen.

Mehr Informationen können unter [Docker Hub](https://hub.docker.com/) gefunden werden.

## Meine LB03

## Befehle
Bei den Befehlen muss man immer UNterscheiden zwischen diesen, welche in ein Dockercompose File und in das Terminal passen.

### Terminal
* docker start + (Docker-ID)
* docker run + (Image)
* Docker run -it + (Image)
* Docker run --net Test –ip 192.168.2.22 -it ubuntu bash 
* Docker container run –name XXX –p 8080:80 
* Docker stop 
* Docker kill
* Docker exec –it + (Docker-ID) (bash/sh) 
* Docker rm $(docker ps –a -q) 
* Docker ps  
* Docker ps -a 
* Docker build -t (Name des Image) . 
* Docker image ls

## Container erstellen
Das Dockerfile kann mit dem Befehl `docker build -t websrv-egli .` erstellt werden. Dabei wird das Dockerfile aus dem lokalen Verzeichniss genommen und für die Erstelung des Images verwendet.

## Starten der Umgebung

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






[Go back to main Document](https://github.com/Daddey69/Modul_300/blob/master/README.md)