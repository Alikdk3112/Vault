---
cards-deck: Operations Research::Erstes Kapitel
---


#### Bestandteile von Optimierungsmodellen #card 
![[Pasted image 20241020141815.png]]




#### Lineares Programm (LP) #card 
- Ein Optimierungsmodell, welches bezüglich der Variablen ausschließlich lineare Beziehungen enthält




#### Graphisches lösen eines Optimierungsmodells #card 

- ![[Pasted image 20241020142657.png]]


#### Abstraktes Modell #card 
- Ein durch allgemeine Parameter formuliertes Optimierungsmodell -> Bei Befüllung mit Werten, erhält man eine **konkrete Modellinstanz**.



#### Integer Program (IP) #card 
- Ein Optimierungsmodell mit ausschließlich **ganzzahligen Variablen**, ist es zusätzlich linear heißt es **ILP (Integer Linear Program)** 
- Bsp: $x_{1},x_{2} \geq 0 \to x_{1},x_{2}\in\mathbb{Z^{+}}_{0}$


#### Mixed-Integer Program (MIP) #card 
- Ein Optimierungsmodell, welches sowohl **ganzzahlige** als auch **kontinuierliche** **Variablen** enthält, ist es zusätzlich linear, heißt es **MILP (Mixed-Integer Linear Programm)**  
- Bsp: $x_{1},x_{2}\geq 0\to x_{1}\in\mathbb{Z^{+}}_{0}, x_{2}\geq_{0}$


#### Big M Bedingung #card 
![[Pasted image 20241020145348.png]]
Aus Nebenbedingung **Big-M** ableiten, einen Werten finden, der so **groß wie nötig** aber **so klein wie möglich** gewählt wird. ->Bei zu großen 𝑀 droht **numerische** **Instabilität**.



#### Modellierungstrick: Implikationen
![[Pasted image 20241020150249.png]]
![[Pasted image 20241020150332.png]]
-> **Beziehungen müssen in einem (M)ILP immer linear sein**

#### Unbeschränkte Variablen #card 
Wenn Variable negativen Wert annehmen kann (Bsp: Vorrat verwenden), kann eine **Unbeschränkte Variable** in 2 Positive Aufgeteilt.
![[Pasted image 20241020151547.png]]

#### Durchführung einer Optimierungsstudie #card 
- ![[Pasted image 20241020152016.png]]
- Im letzten Schritt Einsatz von **Standardsolvern**

#### Standardsolver #card 
- **Spezialisierte Software** die Optimierungsmodelle löst. Moderne Solver bieten **Schnittstellen zu Modellierungssprachen** (AMPL) und **Programmierumgebungen** (Python).
- Solver implementiert verschiedene **exakte und heuristische Optimierungsalgorithmen**, welche abhängig vom Problem **selbstständig** ausgewählt werden können.
- bieten häufig **zusätzliche Funktionen** wie Sensitivitätsanalysen,Parametertuning oder Unterstützung beim Logging
- Beispiele: ![[Pasted image 20241020153809.png]]

#### Klassifikation von Solvern #card 
- ![[Pasted image 20241020153743.png]]

#### Python Syntax Dictionaries: #card 
- Datenstrukturen , die **Schlüssel-Wert-Paare** speichern
- Schlüssel muss **Eindeutig** sein, aber Werte können **mehrfach vorkommen**
```Python
student = {
	"name":"Anna",
	"studiengang": "WIMB"
	"CP": 86,
	"kurse" : ["OR","EWF","Marketing"]
}

print (student["name"]) #Zugriff auf einen Wert mit seinem Schlüssel
student["CP"] = 90 #Wert eines bestehenden Schlüssels ändern
student["age"] = 25 #Einen neuen Eintrag hinzufügen
```

#### For Schleife in Python: #card 
```python
seminargruppe = ["Anna", "Caro", "David"]
for name in seminargruppe:
	print(name)  #Ausgabe: Anna,Caro,David

for i in range(3):
	print(i)  #Ausgabe: 0,1,2
```



