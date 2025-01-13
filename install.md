
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

### Aufruf lokal

http://localhost:17002/


### Reverse-Proxy-Config NGINX

```
upstream 127.0.0.1-compass {
        server 127.0.0.1:17002;
}

server {
        listen   *:80;
        listen   [::]:80;
        
        server_name www.comp-ass-instanz.de;
        
        location / {
                proxy_pass         http://127.0.0.1-compass;
                proxy_redirect     off;
                proxy_set_header   Host $host;
                proxy_set_header   X-Real-IP $remote_addr;
                proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header   X-Forwarded-Host $server_name;
                proxy_set_header   X-Forwarded-Proto https;

        }
        
}
```

Hier drauf aufbauend kann eine SSL-Konfiguration erstellt werden.


### Aufruf 

http://www.comp-ass-instanz.de/

