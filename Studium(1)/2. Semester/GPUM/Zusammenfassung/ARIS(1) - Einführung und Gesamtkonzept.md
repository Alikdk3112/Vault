---
cards-deck: 2. Semester::GPUM::Zusammenfassung
---

# Übersicht zu ausgewählten Formalen Methoden zur Prozessmodellierung #card 
- Formale Methoden lassen sich in Skriptbasierte Methoden (**Skriptsprachen**) und grafische Methoden (**Diagrammsprachen**) unterteilen
- **Skriptsprachen**: Prozessmodelle werden mit ein beschrieben, die sich Programmiersprachen ähneln-->Hohe Präzision erzielbar, anschaulichkeit jedoch gering und setzt Methodenkenntnisse für die Interpretation voraus  $\text{Einsatz in der Praxis folglich erschwert}$ 
- **Diagrammsprachen** lassen sich in
	- **Datenfluss**
	- **Kontrollfluss**
	- **Objektorientierte**
	Ansätze differenzieren
^1727955759549

![[Pasted image 20240621152529.png]]

## Diagrammbasierte Methoden #card 
- ###### Datenflussorientierte Methoden
	-Stellen den **Daten- und Informationsfluss** zwischen Prozessen oder Prozessschritten in den Mittelpunkt--> Prozess wird als Transformation des Datenflusses verstanden.
	Bsp: IDEF-Diagramme, **Datenflussdiagramme (SSA)**
^1727955759558

- ###### Kontrollflussorientierte Methoden
	-Zeitlich logischer Ablauf wird dargestellt. Bsp: Petrie-Netze, **Business Process Modelling Notation (BPMN)**  und **EPK(Ereignisgesteuerte Prozesskette)**

- ###### Objektorientierte Methoden
	-In der Regel zur Softwareentwicklung-> Fachliche Beschreibung von funktionalen Anforderungen an ein Anwendungssystem. Bsp: **Unified Modeling Language**, **Activity Diagramm**
![[Pasted image 20240621155018.png]]


| Modellierungssprache                              | Kurzbeschreibung                                                                                                                                                                                                                                  |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Datenfluss(Structured Systems Analysis -SSA)**  | - Anwendung Klassische Softwareentwicklungsmethode zur Spezifizierung von Informationssystemen                               - Structured Systems Analysis unterstützt mit den Datenflussdiagramm auch die Modellierung von Arbeitsläufen         |
| **UML-Aktivitäts-diagramm**                       | -Anwendung: v.a Gestaltung prozessorientierter Anwendungssysteme                                                                  - Basiert auf Use Case                                                                                          |
| **Business Process Modeling and Notation (BPMN)** | - Anwendung: Modellierung und Dokumentation von Arbeitsabläufen                                                                         -Formale grafische Prozessmodellierungssprache                                                            |
| **Ereignisgesteuerte Prozesskette (EPK)**         | - Anwendung: Fachliche Geschäftsprozessmodelle zur Organisationsgestaltung                                                           - Semi-formale Sprache zur Beschreibung von Prozessen; Abbildung von Prozessen als Ereignisse und Funktionen |
### Beispiele :
- ##### Datenflussdiagramme (SSA) #card 
![[Pasted image 20240621161130.png]]
- ##### UML Notation und Beispiel
![[Pasted image 20240621161217.png]]
- ##### BPMN
![[Pasted image 20240621161249.png]]
---
# EPK
^1727955759562

## Das Aris-Modell
-  Aris = Architektur integrierter Informationssysteme
- Sowohl Methode (Rahmenkonzept) als auch Software (ARIS Toolset) zur Beschreibung von Unternehmen und Anwendungssoftware mit allen wesentlichen Merkmalen
	- Organigramm
	- Fachbegriffsmodell, eRMP
	- Produktbaum
	- Funktionsbaum
	- ###### eEPK (erweiterte Ereignisgesteuerte Prozesskette), WKD (Wertschöpfungskettendiagramm)
- Fokus liegt auf Geschäftsprozess
![[Pasted image 20240621162451.png]]
- ### Datensicht
	- Welche Infos sind wichtig (z.B, Kunde, Lieferant, Produkt, Rechnung)
	- Beschreibung der Informationsobjekte und deren Attribute sowie Beziehungen zwischen Informationsobjekten
	- Darstellung von Ereignissen als Status eines Prozesses
- ### Funktionssicht
	- Welche Funktionen werden ausgeführt ? (Auftragsbearbeitung, Qualitätsprüfung)
	- Beschreibt Beziehungen zwischen Leistungen und Vorgängen, die Leistungen transformieren ($Funktion = Vorgang = Tätigkeit$)
	- Anwendungssysteme, da sie computergestützte Anwendungsregeln von Tätigkeiten festlegen
- ### Organisationssicht
	- welche Organisationseinheiten gibt es ? (Einkauf, Vertrieb, Finanzbuchhaltung)
	- Beschreibung der Aufbauorganisation durch Organisationselemente und Beziehungen
	- Allg. Ressourcen
- ### Leistungssicht
	- Welche Leistungen sind wichtig ? (z.B Kundenzahlung)
	- Strukturiert alle materiellen und immatriellen input und outputleistungen,die in die Geschäftsprozesse eingebracht werden

### **Steuerungssicht**
Beziehung zwischen Daten, Funktionen und Organisationseinheiten

---
## ARIS-Phasenmodell

1. Phase: **Betriebswirtschaftliche Problemstellung**
	- Grobe Tatbestände, die sehr nahe an den fachlichen Zielsetzungen und der fachlichen Sprachwelt orientiert sind 
2. Phase: **Fachkonzept** (Requirements Definition)
	- Detaillerte Modellierung der einzelnen Sichten des Anwendungssystems auf betriebswirtschaftlich-organisatorischer Ebene
	- stellt das zu unterstützende Model in einer formalisierten Beschreibungssprache 
3. Phase : **DV-Konzept** (Design Specification)
	 - Anpassung der Fachmodelle an Anforderungen der Schnittstellen von Implementierungswerkzeugen
4. Phase: **Technische Implementierung** (Implementation Description)
	- DV-Konzept auf konkrete hardware- und softwaretechnische Komponente übertragen

![[Pasted image 20240621181009.png]]

---
# Wertschöpfungskettendiagramme
- 

| Symbol                               | Bennenung                  | Bedutung                                                                                        |
| ------------------------------------ | -------------------------- | ----------------------------------------------------------------------------------------------- |
| ![[Pasted image 20240625130410.png]] | Startfunktion              | Beschreibung einer Funktion, Prozesskette wird initiert auf hohem Abstraktionsniveaus           |
| ![[Pasted image 20240625130622.png]] | Folgefunktion              | Beschreibung einer vorangehenden Funktion auf folgende Funktion, auch auf hohem Abstraktniveaus |
| ![[Pasted image 20240625130943.png]] | Detaillierte Folgefunktion | Wird durch ein anderes Modell nochmal detailliert deswegen extra markiert                       |
| ![[Pasted image 20240625131110.png]] | Nachfolger                 | verknüpft aufeinanderfolgende Funktionen                                                        |
| ![[Pasted image 20240625131146.png]] | Parallel-Prozess           | Verknüpft parallel ablaufe Funktionen einer übergeordneten Haupt                                |
**Hierarchiche Struktur:**
![[Pasted image 20240625131327.png]]
### Beispiel:
![[Pasted image 20240625131405.png]]

---
# Ereignisgesteuerte Prozessketten (EPK)

## Komponenten
##### Knoten:
- **Funktionen:** Verrichtungen oder Aktivitäten verbrauchen *Zeit* und *Ressourcen*
![[Pasted image 20240625131917.png|200]]
- **Ereignisse:** betriebswirtschaftliche Zustände. Bsp: Zeitbezogen ("Monatsanfang erreicht") oder Eintritt von Sachverhalte ("Zahlung eingegangen")
![[Pasted image 20240625131946.png|200]]
- **Verknüpfungsoperatoren:** Verbindung oder Trennung von Prozesspfaden
![[Pasted image 20240625132007.png|200]]

##### Kanten
- Verknüpfung der Knoten miteinander --> Richtung relevant, dargestellt in einem Pfeil

### Verknüpfungsoperatoren
 - **UND**: $\wedge$ *Allen* ausgehenden Prozesspfaden muss gefolgt werden. Wenn einer der Pfade noch nicht vollständig durchlaufen wurde, so wird erst fortgeführt, bis alle Prozesspfade durchlaufen wurden
 - **Offenes ODER:** $\vee$ *Mindestens einem* der Möglichen Prozesspfade muss gefolgt werden
 - **Exklusives ODER:** $XOR$ oder $X$ *Genau einem* der möglichen Prozesspfade muss gefolgt werden
 - Vernüpfungen können miteinander verbunden werden.

## Modellierungsregeln
- Eine EPK wird durch ein Ereignis ausgelöst und endet mit mindestens einem Ereignis
- Ereginisse werden mit Funktionen verknüpft, entweder als **Auslöser** oder als **Egebnis**
- **Alternierende Folge** von Ereignissen und Funktionen: Ereignis/Funktion/Ereignis
- Funktionen und Ereignisse können nicht nicht mehr als eine **eingehende** und eine **ausgehende** **Kante** besitzen 
- Verknüpfungsoperatoren ---> **Zusammenführen** von Pfaden: **Beliebig viele Pfade möglich**
- **Nach Ereignisse keine Entscheidungen treffen**, die den weiteren Prozessverlauf beeinflussen
- Nach einzelnem Ereignis darf kein logischer Verknüpfungsoperator folgen, der eine Entscheidung erforderlich macht (kein OR, kein XOR)
- Entscheidungen in Funktionen treffen

#### Zerlegung von Ereignissen
![[Pasted image 20240625163802.png]]
- Kundenauftrag liegt vor wird zerlegt in Kunde erteilt auftrag per $X$

#### Parallele Abläufe 
![[Pasted image 20240625163932.png]]
-  Abläufe können Parallel ablaufen

#### Alternative Abläufe
![[Pasted image 20240625164118.png]]
Entweder Linker Pfad oder Rechter Pfad wird durchgeführt


### Modellierungsregeln in Aris 
![[Pasted image 20240625164314.png]]
- **Syntax**(Grammatik): Modellierungsregeln für die Struktur von EPKs und deren Einhaltung
- **Semantik**(Bedeutung): Korrekte/sinngemäße Abbildung eines (verbal) beschriebenen Geschäftsprozesses
 ---

## Referenzmodelle
- **Definition**: versteht man konkrete, aber vom Unternehmenseinzelfall abstrahierte Modelle zur Darstellung von technischen oder betriebswirtschaftlichen Fachinhalten bezüglich der Strukturen und Abläufe
- Sie gelten für eine Klasse von Objekten
	- besitzen höhren Abstraktionsgrad als (unternehmens-) spezifische Modelle
	- Beinhalten häufig größere Anzahl von Teilmodell-Alternativen, die unterschiedliche (Unternehmens-) Szenario wiedergeben

- können auf einer **technischen Ebene** angesiedelt sein oder einen **betriebswirtschaftlichen Domännenbezug** aufweisen. 
	- **Technische Ebene**: ISO-OSI Schichtenmodell
	- **betriebswirtschaftlichen Domännenbezug**: Referenzmodell für Industriebetriebe von Scheer

-  Ein Referenzmodell entsteht **induktiv** durch die Konsolidierung von Know-how aus vorhandenen Modellen, Anwendungssystem-Dokumenationen, Fachkonzepten usw oder Wird **deduktiv** aus theoretischen Erkenntnissen in der Argumentationskette abgleitet

### Vorteile und Beispiele zu Referenzmodellen
- Mit einem Referenzmodell wird das abgebildete Wissen über **"best practice"** oder **"common practic"** auf das Unternehmensspezifischere Modell übertragen
- Durch die Verwendung von Referenzmodelllen als Basis der Modellherstellung wird die **Qualität** erhöht und der Prozess der **Modellerstellung beschleunigt**

# Zusammenfassung
- Prozesse sind auf **unterschiedlichen** **Abstraktionsniveaus** modellierbar, von Prozesslandkarten bis zu einzelnen Bearbeitungsvorgängen
- **Wertschöpfungskettendiagramme** dienen eher zur Modellierung der **Grobstruktur** von Geschäftsprozessen, **EPKs** eher für die **Feinstruktur**
- **Referenzmodelle** stellen Hilfe als **Best Practices** bei der gestaltung spezifischer Modelle (unternehmensspezifisch)
