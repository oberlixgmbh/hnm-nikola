# hnm-nikola [![Build Status](https://travis-ci.org/fablabnbg/hnm-nikola.svg?branch=master)](https://travis-ci.org/fablabnbg/hnm-nikola)
Nikola Sourcen der Homepage der Hack &amp; Make 2020


## Wie kann ich was ändern?

* Ihr benötigt einen github-Account. Falls Ihr noch keinen habt, der ist schnell eingerichet.
* Dann benötigt ihr Schreibrechte in der fablabnbg-Organization oder zumindest in diesem Repository hier.
Dazu schickt einfach euren github-Benutzernamen an ian. (Zum Beispiel, indem Ihr einfach hier ein neues "Issue" eröffnet).
* Dann könnt Ihr hier lokal über das "Stift"-Icon die Seiten ändern.
  * Die Seiten liegen alle im Unterverzeichnis "pages".
  * Ändern von Seiten hier ist für einfache Änderungen am Text das einfachste.


## Wie kann ich lokal ändern oder neue Seiten hinzufügen?

* Wenn Ihr Änderungen am Design vornehmen wollt oder Neuigkeiten oder Seiten hinzufügen wollt, installiert ihr am besten Nikola lokal.
* Installationsanleitung unter Linux:
  1. python3 verwenden/ggf. installieren: `sudo apt install python3-pip`
  1. virtualenv installieren: `pip install virtualenv` -- **bitte unbedingt darauf achten, dass ihr python3 verwendet**. Ggf. dazu `pip3` anstelle von `pip` eingeben. 
  1. Erstellt ein neues leere Unterverzeichnis und wechselt dort hin. (Zum Beispiel `mkdir nikola && cd nikola`)
  1. Erstellt ein virtualenv in diesem Verzeichnis: `virtualenv .`
  1. Aktiviert das virtualenv: `source bin/activate`
  1. Installiert nikola: `pip install nikola[extras]`
  1. Holt Euch die Sourcen der Webseite: `git clone https://github.com/fablabnbg/hnm-nikola.git`
  1. Wechselt ins Unterverzeichnis: `cd hnm-nikola`
* Ändern/neu erstellen (unter Linux):
  1. Wechselt in eurer nikola-virtualenv-Verzeichnis
  1. Aktiviert das virtualenv: `source bin/activate`
  1. Wechselt ins Unterverzeichnis: `cd hnm-nikola`
  1. Dort könnt ihr nun die diversen Dateien nach Euren Wünschen und mit einem Editor Eurer Wahl (vim, VS Code, kate, ...) anpassen
  1. Zum neuerstellen der Seiten: `nikola build`
  1. Zum lokalen Anschauen der Seiten: `nikola serve -b`
  1. Zum deployen der erstellten Webseite auf dem Testserver: `nikola github_deploy`
  1. Zum speichern der Änderungen an den Sourcen auf github:
     1. Ggf. Auflisten der geänderten Dateien mit `git status`
     1. Alle geänderten Dateien zum comitten vormerken: `git add .`
     1. Ggf. Anzeigen der Änderungen mit `git diff`
     1. Änderungen comitten: `git commit -m "<Änderungsbeschreibung>"`
     1. Den Commit auch auf dem remote-Server (=github) speichern: `git push`


## Verbesserungsvorschläge/Änderungswünsche

Verbesserungsvorschläge oder Änderungswünsche meldet Ihr am besten einfach hier als "New Issue" an.

## Technische Details

### Nikola Config

* liegt in `conf.py`
* Theme ist das Standard-Theme für Webseiten: "bootstrap4" und bist jetzt unverändert.
* Anpassung des Design liegt in `files/assets/css/custom.css`
  * Gemäß Hack & Make CI von 2017 wird die Hintergrundfarbe auf rot #C01A2C gesetzt und der Font ist "Coolvetica".
  * Konfiguration folgt der Anleitugn für Webseiten (anstelle eines Blogs): https://getnikola.com/creating-a-site-not-a-blog-with-nikola.html

### Deployment (lokal):

* Zur Zeit erfolgt das Deployment in Richtung github-pages
  * github verwendet dazu automatisch das, was im Branch `gh-pages` abgelegt ist
  * Diese sind erreichbar unter https://fablabnbg.github.io/hnm-nikola
  * Allgemeine Anleitung für [github-pages](https://help.github.com/en/github/working-with-github-pages/about-github-pages)
* TODO: Deployment auf eigenen Server
  * Wird sinnvollerweise über rsync mittels ssh-key erfolgen.

### Deployment (travis-ci)

* travis-ci ist ein Continious-Integration Dienst. Sobald eine Änderung auf github committed (oder remote "gepusht") wird, führt travis-ci die in der Datei `.travis.yml` hinterlegten Befehle aus.
  * siehe https://travis-ci.org/fablabnbg/hnm-nikola
* In diesen Befehlen ist zur Zeit hinterlegt:
  * Eine frische Installation von nikola (da travis allerdings die Build-Umgebung cached, wird diese nicht jedes mal ausgeführt)
  * ein Bauen der Seite (`nikola build`)
  * Ein Deployment der Seite auf github.io 
    * Dazu wird die unter "Deployment (lokal)" beschriebene Konfiguration verwendet
    * Das Projekt hat dazu einen eigenen ssh-key, dessen public-Teil auf github hinterlegt ist (siehe "Settings" im Repository)
    * Der private Teil ist verschlüsselt gespeichert. Den symmetrischen Schlüssel zum entschlüsseln kennt wiederum nur travis-ci.
    * Anleitung dazu https://getnikola.com/blog/automating-nikola-rebuilds-with-travis-ci.html
