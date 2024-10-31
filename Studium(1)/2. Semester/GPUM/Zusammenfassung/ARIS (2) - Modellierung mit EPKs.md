---
cards-deck: 2. Semester::GPUM::Zusammenfassung
---

## Grundstruktur eines Geschäftsprozesses #card 

![[Pasted image 20240626130510.png]]
^1727955313213

### Sichtenkonzept zur Reduktion von Komplexität in der Prozessmodellierung #card 
- Häufig sinnlos, alle modellierungsrelevante in einer einzigen Darstellung abzubilden
- Zur *Reduktion* *der* *Komplexität* und *zur Verbesserung der Verständlichkeit und Transparenz*´der Modelle empfiehlt sich die Anwendung eines **Sichtenkonzeptes**
- Unterscheidung nach **Prozess- und Struktursichten**
	- Die **Prozesssicht** beschreibt die an einem Prozess beteiligten Modellierungsobjekte aus ablauforientierter Sicht
	- **Struktursichten** beschreiben die Struktur der Modellierungsobjekte, die in der Prozess-Sicht zusammengeführt werden
^1727955313217

#### Struktursichten #card 
![[Pasted image 20240626131047.png]]
### Zusätzliche Komponenten einer EEPK
^1727955313219

- **Organisationseinheiten**
	- **Stellen** oder auch **konktrete** **Personen** sind die **Träger der Funktionen**. sie können dabei in Bezug auf die Funktion unterschiedliche Rollen einnehmen
- **Anwendungssysteme**
	- meist Software **unterstützen die Ausführung** der Funktionen und speichern die notwendigen Daten bzw Stellen diese für Prozesse bereit
- **Daten** 
	- Daten stellen de Input bzw Output von Funktionen dar. Ggf können **Dokumente** als Datenträger modelliert werden

- **Leistungen**
	- Sind das **Ergebnis on Prozessketten** oder einzelnen Prozessschritten bzw werden von diesen verarbeitet
	- Leistungen können z.T mit Dokumenten, die Bestandteil einer Leistung sind, identisch sein, bsp "Kundenauftragsbestätigung" oder "Bestätigungsschreiben"
- **Kantentypen**
	- in eEPK können verschiedene Kantentypen verwendet werden, die jeweils eine konkrete Bedeutung (Semantik) besitzen
	- Beispiele :
		- Rollen- "ist fachlich verantwortlich für" oder "Wirkt mit"
		- Daten, Dokumente - "Ist Input für " oder "ist Output für"
		- Leistungen - "ist Ergebnis von"
		- Anwendungssystem- "unterstützt"
## ARIS Haus mit EEPK
![[Pasted image 20240626132728.png]]

# EEPK
#### Wesentliche Elemente
![[Pasted image 20240626132921.png]]
-  **Daten** (*Hellblau*) --> werden in Funktionen verarbeitet
- **Mitarbeiter** (<span style="color:#ffff00">gelb</span>) --> Mitsrbeiter sind veranwortlich für Funktionen
- **Organisationseinheiten** (<span style="color:#ffff00">gelb und rund</span>) --> Mitarbeiter gehören denen an
- **Leistungen** (<span style="color:#00b050">hellgrün</span>) --> Funktionen erzeugen und verarbeiten Leistungen
---
## Funktionssicht

![[Pasted image 20240626133404.png]]
- **Zweck und Struktur von Funktionen**
	- Ein **Funktionsbaum** dient der Darstellung des hierarchischen Aufbaus der in einem Unternehmen bzw Unternehmensbereich anfallenden Funktionen
	- Eine komplexe Funktion kann in Unterfunktionen zerlegt werden
	- Zerlegung wird mit Hilfe des Funktionsbaums (reines Hierarchiediagramm grafisch dargestellt)
- **Was ist eine Funktion**
	- **Träger von Zeit und Kosten** 
	- fachliche Aufgabe , Vorgang bzw Tätigkeit an einem (Informations)
	- ![[Pasted image 20240626134346.png]]
![[Pasted image 20240626134402.png]]


## Organisationssicht
![[Pasted image 20240626134635.png]]

- **Zweck eines Organigramms:**
	- **Aufbauorganisation** eines Unternehmens wird dargestellt. Je nach Strukturierungskriterien die gebildeten Organisationseinheiten und ihre Verknüpfungen werden untereinander dargestellt
- **Organisationseinheit ?**
	- Träger der zur Erzielung der Unternehmensziele durchzuführenden Aufgaben.
	![[Pasted image 20240626134944.png]]

### Stellen, Personen und Gruppen
-  Eine **Stelle** ist die kleinste zu identifizierende Organisationseinheit im Unternehmen. Die verantwortlichkeiten und Weisungsbefugnisse werden in der jeweiligen Stellenbeschreibung festgelegt
- **Personen** sind die konkreten Mitarbeiter eines Unternehmens, können **Stellen** besetzen oder **Organisationseinheiten** direkt zugeordnet werden
- **Gruppe** stellt die Gruppierung von Mitarbeitern / Personen dar, die z.b zur Lösung einer bestimmten Aufgabenstelung für einen bestimmten Zeitraum zusammenarbeiten (z.b Projektgruppe).
![[Pasted image 20240626141823.png]]
## Datensicht
![[Pasted image 20240626141907.png]]
-  **Fachbegriffsmodell** beschreibt die einheitlichen Begriffe von Datenobjekten (*"Eindeutige Begriffssystematik"*) und dient der Kommunikation
- **Datencluster** ist eine *logische Sicht auf mehrere Fachbegriffe und deren Beziehungen* untereinander
- dient häufig als als Input/Output
![[Pasted image 20240626142227.png]]
---
## Entitiy-Relationsship-Modell (ERM)
- Dient zur detaillierten und formal strengen Datenmodellierung, vor allem der Beziehungen der Datenobjekte untereinander

| **Symbol**                           | **Bedeutung**                                                                                                                                                                                                         |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![[Pasted image 20240626142513.png]] | enthält eine Menge Entitäten desselben Typs, d.h sie besitzen die gleichen Eigenschaften--> *Namenskonvention*: Es ist die Bezeichnung des jeweiligen Entitätstyps anzugeben. Zum Beispiel "Auftrag"                  |
| ![[Pasted image 20240626142636.png]] | Stellt Beziehungen zwischen einzelnen Entities dar --> *Namenskonvention*: An dieser Stelle ist ein Verb anzugeben, dass die Beziehung zwischen mehreren Entitätstypen eindeutikg charakterisiert. Zum Beispiel "hat" |
![[Pasted image 20240626142901.png]]

---
## Grundsätze Ordnundsmäßiger Modellierung (GOM) - Hintergrund
-  Anspruch: Modelle, die von unterschiedlichen Modellierern entwickelt werden, müssen vergleichbar und ggf. einfach konsolidierbar sein
- **Ordnungsrahmen** der die Erstellung von Prozessmodellen in Bezug auf Klarheit, Konsistenzsicherung und Qualität unterstützt
- In Anlehnung an die **Grundsätze ordnungsmäßiger Buchführung**
- Überall dort anwendbar, wo allgmeine Modellierungsregeln nicht mehr Ausreichen
- Geben Empfehlungen für eine "gute" Modellierung, z.B. für 
	- Beginn und den eines Prozesses
	- den Detaillierungsgrad
	- die Einbettung in einen Ordnungsrahmen
	- die Verständlichkeit
![[Pasted image 20240626143616.png]]
**Notwendige Grundsätze**
- Grundsatz der Richtigkeit
- Grundsatz der Relevanz
- Grundsatz der Wirtschaftlichkeit
**Ergänzende Grundsätze**
- Grundsatz der Klarheit
- Grundsatz der Vergleichbarkeit
- Grundsatz des systematischen Aufbaus
$-\to\text{GoM}$

- ##### Fallbeispiele 139 zur Übung

# Zusammenfassung und Ausblick
- eEPKs beeinhalten neben der **Steuerungssicht** weitere Sichten: **Funktionssicht**, **Organisationssicht**, **Datensicht** und **Leistungssicht**
- Grundsätze Ordnungsgemäßiger Modellierung geben dir einen **Ordnungsrahmen** vor, der die Erstellung von Prozessmodellen in Bezug auf Klarheit, Konsistenzsicherung und Qualität 
---
