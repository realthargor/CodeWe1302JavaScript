 CodeWe1302JavaScript
====================

Coding Weekend Project 2013-02 JavaScript Framework Evaluation

# Einführung

## Projektmotivation 

Für mehrschichtige Applikationen (Multitier Enterprise Applications)
werden zur Umsetzung der Frontends traditionell die Technologien der
Sprachen (Java, .NET) gewählt, welche in der Middleware zum Einsatz
kommen. Dabei handelt es sich meist um "Serverside"-Technologien, die
einen State verwalten ein Templating bereitstellen und den vollen
Umfang der Middleware-Sprache zur Verfügung haben.

Als Folge davon entstehen Frontends die bei jedem Seitenwechsel einen
Request/Responce-Zyklus durchlaufen und häufig einen Teilaspekt der
Geschäftslogik abbilden.

Ziel bei der Entwicklung von Frontends sollte es sein, dass sie
ausschliesslich Logik beinhalten, die die Navigation und Anzeige von
Frontend-Elementen behandelt und möglichst wenig Anfragen zum Server
gesendet werden, um dem Anwender ein flüssiges Arbeiten zu erlauben.
Siehe auch RAI: https://de.wikipedia.org/wiki/Rich_Internet_Application

Zur Umsetzung einer solchen RAI stehen eine Vielzahl an JS-Frameworks
zur Verfügung.

Aktuell ist die mögliche Auswahl an verfügbaren und aktuellen
Frameworks, welche auf JavaScript (JS) setzen, in der Tat so hoch,
dass die genauen Vor- und Nachteile der einzelnen Lösungen
hinsichtlich Verfügbarkeit und Aktualität der Projektdokumentation,
Einarbeitungszeit, Dauer und Qualität des Framework-Lifecycles, sowie
deren technische Eleganz bei der Implementierung, nicht bekannt oder
hinreichend dokumentiert vorzufinden ist.

Um eine Entscheidungsbasis über die allgemeine Reife für den Einsatz
in industriellen Großprojekten zu etablieren, oder gar die
Entscheidung für eine bestimmte Kombination an JavaScript-Rahmenwerken
zu ermöglichen soll ein Vergleich diverser JS-Frameworks pragmatisch
vollzogen werden.

## Grundidee

Evaluierung ausgewählter JavaScript-Frameworks durch Realisierung
einer äquivalenten Testanwendungen.

Vergleiche hierzu ähnliches Projekt mit ToDo-App als Referenz:
http://addyosmani.github.com/todomvc/

## Erwartete Funktionalitäten von JS-Frameworks

Gemeinsamkeiten (Häufige Standards):

- Templating
- Model-Binding
- Pageflow, Routing
- Messages, REST
- JS Dokumentation

### Kandidaten

* AngularJS (http://angularjs.org/) 
* Backbone.js (http://backbonejs.org/) 
* Ember.js (http://emberjs.com/)
* Knockout (http://knockoutjs.com/)
* JavaScriptMVC (http://javascriptmvc.com/) 

## Beschreibung der Testanwendung

### Geschäftsprozess

Kundenerfassung mit Personendaten, Adressdaten und Bestätigung der gemachten Angaben.

### Seiten+Felder

Personendaten (Page):

- Name und Vorname: Text-Fields (required)
- Geburtstag: Date-Field mit DatePicker (required)
- Kreditkarten Nummer: Number-Field (required, genau 10-stellig)

Adressdaten (Page):

- Land: Drop-Down-Box (required, mit Default-Wert)
- Strasse und Hausnummer: Text-Field und Number-Field (required)
- PLZ und Ort: Number-Field (Validierung mit automatischer Befüllung des Ortes)
- Wohnhaft seit: Date-Field mit DatePicker (required)
- if (Wohnhaft seit) < 2 Jahre: Neue Adressegruppe mit vorheriger Adresse (Toogle show/hide)

Zusammenfassung (Page):

- Datenwiedergabe (Labels, Output Fields)
- Datenbestätigung (Checkbox)
- Submit (Gemockter REST-Call zum Backend)

Ende (Page):

- Danke (Text)
- Neubestellung (Link zu Personendaten, Loop)

# Umsetzung

## Ergebnisse

Die Dokumentation und ein ausführlicheres Fazit findet sich im jeweiligen Repo.

* AngularJS 
  - https://github.com/dataduke/CodeWe1302AngularJs
* Backbone.js
  - https://github.com/sebastianfuss/backbone-test
* JavaScriptMVC
  - https://github.com/realthargor/javascriptMVCCodingWe

## Zusammenfassung und Fazit

Zusammenfassend lässt sich sagen, dass zu unserer Überraschung der
Abstand zwischen den untersuchten Frameworks riesig ist. Mit dem
richtigen Framework lässt sich die beschriebene Testanwendung ohne
vorherige Erfahrung in zwei Tagen vollständig umsetzen, mit dem
Falschen wird es zum Martyrium.

AngularJS geht als eindeutiger Sieger hervor. Es ist ordentlich
dokumentiert und erlaubt es in relativ kurzer Zeit eine fast
vollständige Anwendung mit Boardmitteln zu realisieren ohne eine
unnötige Komplexität mitzubringen. Der erzwungene Codestil (es wird
mit spezifischen Attributen an Tags gearbeitet) kann durchaus
kontrovers diskutiert werden. Unter der Prämisse das Frontends
ausschliesslich Anzeigelogik enthalten sollen und ihr Model direkt auf
die gezeigte Ansicht zugeschnitten sind, ist es jedoch durchaus valide Lösung.

Auch mit Backbone.js dem Zweitplazierten war es möglich eine
vollständige Anwendung zu entwickeln. Hierzu musste aber aus einer
Vielzahl von Erweiterung für die unterschiedlichen Aufgaben ausgewählt
und eine Integration der Plugins geschaffen werden. Ingesamt ist dabei
deutlich mehr Code entstanden als bei AngularJS, was unter dem Aspekt
der Wartbarkeit durchaus kritisch zusehen ist.

Der Verlierer (nein kein dritter Platz!) JavascriptMVC hat es Aufgrund
der vielen Bugs der schlechten Dokumentation und es geringen
Funktionsumfangs nichtmal in die Qualifikation geschafft.

## Referenzen

### Unterstützende Frameworks

- jQuery (http://jquery.com/), jQueryUI (http://jqueryui.com/), QUnit (http://qunitjs.com/) : Einige JS Frameworks bauen darauf auf (Dependencies)
- PrototypeJS (http://prototypejs.org/) : Sammlung von JavaScript-Basisfunktionalitäten; wird in  Kombination mit jQuery und Backbone.js häufig verwendet
- Bootstrap (http://twitter.github.com/bootstrap/) : Utility-Framework für Layout, HTML, CSS etc. 
- Underscore.js (http://underscorejs.org/) : Utility-Framework, welches grundlegende Hilfsfunktionen liefert (vgl. Java Commons API)
- Docco (http://jashkenas.github.com/docco/) : Codedokumentation
- Node.js (http://nodejs.org/) : Event-driven I/O server-side JavaScript environment
- RequireJS (http://requirejs.org/) : Module and File Loader for JS, verwendet bei einigen JS Frameworks (Dependencies)
- DocumentJS (http://javascriptmvc.com/docs.html#!/search/DocumentJS) : Codedokumentation
- StealJS (http://javascriptmvc.com/docs.html#!steal) : Collection of command line and JS client utilities that make building, packaging, and sharing JS applications
- FuncUnit (http://javascriptmvc.com/docs.html#!FuncUnit) : Testing of web applications with a simple jQuery-like syntax via integration with Jasmin (behavior-driven development framework), Selenium (capture and replay tool) and PhantomJS (headless WebKit with JavaScript API with support for  DOM handling, CSS selector, JSON, Canvas, and SVG) and automated QUnit tests (unit testing).

### Tools und Literatur

- JS Editoren/IDEs: 
    - WebStorm (http://www.jetbrains.com/webstorm/) : Kommerzielle IDE
    - NetBeans (http://netbeans.org/) : Open Source IDE
    - Cloud9IDE (https://c9.io/) : Online Editor mit Konsole und Repo-Anbindug nach GitHub, BitBucket etc.
    - Sublime Text (http://www.sublimetext.com/) : Kommerzieller Editor
    - Vim (http://www.vim.org/) oder Emacs (http://www.gnu.org/software/emacs/) : freie, stark erweiter- & konfiguierbare Editoren
- JS Web Tools:
    - JSFiddle (http://jsfiddle.net/) : Online Editor with Code Sharing
    - cdnjs (http://cdnjs.com/) : Online hosted JS libraries/frameworks
    - Google CDN (https://developers.google.com/speed/libraries/devguide) : Online hosted libraries
    - Microsoft CDN (http://www.asp.net/ajaxlibrary/cdn.ashx) : Online hosted libraries
- Books: 
    - JavaScript Patterns (Stoyan Stefanov)

