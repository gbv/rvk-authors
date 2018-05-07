# Mapping von Klassen zur Autor*innen mit GND und Wikidata

Die RVK enthält eine Reihe von Klassen zu einzelnen Autoren. Für diese können 1-zu-1 Mapping zu anderen Normdateien ermittelt werden, insbesondere GND und Wikidata.

## Beispiel

* RVK: [BD 4006 - BD 4007 Aaron ben Elijah (1328-1369)](https://rvk.uni-regensburg.de/regensburger-verbundklassifikation-online#notation/BD%204006%20-%20BD%204007)
* GND: <https://d-nb.info/gnd/104076682>
* Wikidata: <https://www.wikidata.org/wiki/Q302956>

## Arbeitsschritte

1. Ermittlung der RVK-Klassen zu einzelnen Personen
2. Kontextualisierung durch übergeordnete Klassen (z.B. "Das Judentum im Mittelalter") um Personen mit gleichem Namen besser unterscheiden zu können.
3. Mapping (z.B. Wikidata mix'n'match)

Um das Mapping nach Aktualisierungen wiederholen zu können, sollten die Arbeitsschritte möglichts automatisiert ablaufen. 

## Umsetzung

Personenklassen strehen anscheinend immer Unter einer Klasse mit einer Benennung wie "Autoren A", "Autoren B" etc. Weitere Personen gibt es unter Klassen wie "Autoren und Denkmäler V" allerdings sind darunter auch andere Entitäten. Aus JSKOS lassen sich diese Überklassen so ermitteln:

    jq -c 'select(.prefLabel.de|match("^Autoren [A-Z]$"))' rvk.ndjson

Von diesen 2114 Klassen (Stand Dump 01/2018) sollten sich alle direkten Unterklassen auf einzelne Autoren beziehen. 

    ...TODO: weiteres jq-Skript...

Etwas komplizierter ist die Kontextualisierung der Personen-Klassen.

...TODO...

Die Mappings werden zunächst in Wikidata eingetragen. RVK-Wikidata-Mappings werden jetzt schon täglich abgerufen: <http://coli-conc.gbv.de/concordances/wikidata/>.

