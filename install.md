
![ComP-ASS](headerLogo.svg)

### Computergestütztes Lernen und Lehren im Handwerk mit interaktiven Assistenzsystemen

## Installation

Das ganze Projekt ist in einem .tar.gz-File zusammengefasst.
Dieses kann auf einem Docker-fähigen Linux-Server entpackt werden.

```
mkdir -p /srv/docker
cd /srv/docker
wget https://sequoia.handwerk-comp-ass.de/00-for-github/comp-ass.tar.gz
tar -xzf comp-ass.tar.gz
cd comp-ass
docker compose up -d
```

Die Web-Anwendung ist dann über den localhost-Port 17002 erreichbar.
Dieser kann über eine reverse-Proxy-Konfiguration eines lokal installierten NGINX erreichbar gemacht werden.

### Konfiguration

im Ordner src/global liegt die Datei "inc.global.php" in welcher der Hostname und einige Settings eingetragen werden.