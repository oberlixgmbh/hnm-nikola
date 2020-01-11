# hnm-nikola
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
* Anleitung unter Linux:
  1. python3 verwenden/ggf. installieren: "sudo apt install python3-pip"
  1. virtualenv installieren: `pip install virtualenv` -- bitte unbedingt darauf achten, dass ihr python3 verwendet. Ggf. dazu `pip3` anstell von `pip` eingeben. 
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
  1. Dort könnt ihr nun die diversen Dateien nach Euren Wünschen anpassen
  1. Zum neuerstellen der Seiten: `nikola build`
  1. Zum lokalen Anschauen der Seiten: `nikola serve -b`
  1. Zum deployen auf dem Testserver: `nikola github_deploy`
  1. Zum speichern der Änderungen auf github:
     1. `git add .`
     1. `git commit`
     1. `git push`
   
  


## Verbesserungsvorschläge/Änderungswünsche

Verbesserungsvorschläge oder Änderungswünsche meldet ihr am besten einfach hier als "New Issue" an.
