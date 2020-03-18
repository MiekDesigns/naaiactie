# Naaiactie

Bijdrage leveren? Dat kan!
* Maak een fork en een pull request.
* Meld problemen via de [issues](https://github.com/MakeInBelgium/naaiactie/issues/new).

## Deployment

Site is beschikbaar in 2 verschillende talen:
- NL: https://maakjemondmasker.be/
- FR: https://faitesvotremasquebuccal.be/
- EN: https://makefacemasks.com/

Het is een *onepager* en iedere taal heeft zn eigen index bestand:
- index_nl.html
- index_fr.html
- index_en.html

De website wordt gehost bij cloudz.be. Daar draait een script dat iedere 5 minuten een `git pull` doet van deze repo.
Hou er rekening mee dat Cloudflare alles cached. Bij een update moet de cached geïnvalideerd worden.

```bash
# Stuur je public key naar @iworx
ssh coronade@da-2.cloudz.be
```

## Kom er bij!
Neem dan deel aan de conversatie op de Slack workspace van de Corona-denktank Make in Belgium: https://join.coronadenktank.be (Kanaal: #project-corona-naaiactie-dev).


# local server
Zelf een lokale server opzetten? Dat kan op verschillende manieren!

## met python
Eenvoudig lokaal previewen met het terminal-commando: `python3 -m http.server 8000` (of `python -m http.server 8000` als python 3 je standaardpython is)
De Naaiactie is vervolgens bereikbaar op `http://localhost:8000`

## met php
Heb je php op je computer geïnstalleerd? Gebruik dan de PHP built-in webserver:

```
$> php -S 0.0.0.0:8000
```

De Naaiactie is vervolgens bereikbaar op `http://localhost:8000`

## met docker
Gebruik de `Dockerfile` om een image te builden. Zie `docker-run.sh` voor een voorbeeld van hoe het in productie wordt gedraaid. Hiervoor gebruiken we een set-up met Traefik, voor de config, zie de repository van [solidariteitsnetwerk](https://github.com/MakeInBelgium/solidariteitsnetwerk/tree/master/deployment).


# CSS
De css wordt gegenereerd met bootstrap in de npm dependencies, dit kan via het commando `npm ci`. Vervolgens kan je in de map `assets/css` met [SCSS](https://sass-lang.com/) de SCSS converteren naar CSS:

**Dev (met auto refresh)**

```
scss --watch assets/css/style.scss assets/css/style.css
```

**Prod (voor een push)**

```
scss --style compressed assets/css/style.scss assets/css/style.css
```

# PDF met handleiding + patroon
Je kan de verschillende versies van de patronen vinden in de /pdf folder.
Bij het aanpassen van de huidige versie van een patroon best volgende stappen doorlopen:

* Voeg versienummer en eventueel datum toe aan de naam van het document
* Zorg ervoor dat de grootte van het document zeker kleiner is dan 1 MB (om onze bandbreedte te vrijwaren). Haal daarom je versie altijd nog eens door de website http://www.pdfcompressor.com
* Er zijn al problemen geweest met Adobe Reader. Probeer zeker af te checken of je nieuwe PDF ook daarin goed te lezen valt.
