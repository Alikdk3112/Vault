# Ansatz

Problem ist leicht, wenn es in Polynomialzeit lösbar ist
Worst-Case-Laufzeit des Algorithmus ist also $\theta\left( \sum_{i=0}^k a_{i}n^i\right)=poly(n)$ mit konstanten $a_{i},k$

Leicht zu lösende Probleme:
- Sortieren eines Arrays
- Breitensuche im Graphen
- Minimlae Spannbäume berechnen
- ...
Probleme mit leicht zu überprüfender Lösung:
- TSP
- Faktorisieren
- ....
Unentscheidbare Probleme
- Halteproblem
- Code-Erreichbarkeit
- ...
# Berechnungsprobleme vs Entscheidungsprobleme

**Berechnungsproblem:**
Gegeben: Problem $P$
Gesucht: Lösung $S$
Beispiel: Berechne kürzeste Pfade im Graphen

**Entscheidungsproblem:**
Gegeben: Problem $P$
Gesucht: hat $P$ Eigenschaft $E$ ? wahr falsch antwort
Beispiel: ist gerichteter Graph stark Zusammenhängend ?

Man Kann jedes Berechnungs-in ein Entscheidungsproblem überführen, so dass Polynomialzeit-Lösung für Berechnungsproblem ergibt.

## Beispiel Faktorisierem
![[Pasted image 20240802200106.png]]
![[Pasted image 20240802200129.png]]
