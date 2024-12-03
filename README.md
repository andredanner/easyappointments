  :sparkles:  :muscle: :muscle: :muscle:   :sparkles: 
#How to set up easyappointments!

This is the home of the intellectual property of co-brainers.


## Components

nginx: Webserver and loadbalancer, listens at port 80 to route into the appointments backend

PHP-FPM (FastCGI Process Manager) ist eine alternative Implementierung von PHPs FastCGI, die für besonders stark frequentierte Websites und Anwendungen entwickelt wurde. Es handelt sich um eine Komponente, die PHP-Skripte effizienter ausführen kann, indem sie eine Verbindung zwischen dem Webserver und PHP herstellt. Hier sind die wichtigsten Merkmale und Funktionen von PHP-FPM:
Wie funktioniert PHP-FPM in einem typischen Setup?
Webserver (z. B. Nginx, Apache) empfängt HTTP-Anfragen.
Der Webserver reicht PHP-Skripte an PHP-FPM weiter, indem er sie an einen FastCGI-Socket sendet.
PHP-FPM verarbeitet die Skripte und liefert die Ergebnisse (HTML, JSON, usw.) an den Webserver zurück.
Der Webserver gibt die Antwort an den Client (Browser, API-Aufrufer) weiter.

mysql-DB-Server: Host für unsere DB Instanzen - jeder Kunde hat eine eigene Instanz

## Installation

Alle Komponenten werden als Docker-Container aufgesetzt, wobei wir nur das Dockerfile des php-fpm für das bauen
eines Images benutzen.

Nginx und mysql sind bei Basisimages, die wir 1:1 nutzen, wie auf dem Docker-Hub verfügbar.

###
```bash
https://github.com/alextselegidis/easyappointments
docker build -t appointments:v1.5_01 ./docker/php-fpm
docker run --cap-add net_raw --cap-add net_admin --name=php-fpm   -v .:/var/www/html   -e LOG_LEVEL=debug --network=mynet   -e DB_HOST=mysql -e DB_NAME=mysql   -e DB_USERNAME=root -e DB_PASSWORD=Zumwinkel123@   -d appointments:v1.5_01

```

## Nuggets

- The regex pattern used for the classification of appointments is \

