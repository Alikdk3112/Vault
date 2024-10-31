## Auswahl algorithmischer Entwurfmethoden

### Divide & Conquer
löse Rekursiv (disjunkte) Teilprobleme
siehe Quicksort,Merge Sort

### Backtracking
Durchsuche iterativ Lösungsraum

### Dynamisches Programmieren
Löse rekursiv (überlappende) Teilprobleme durch Wiederverwenden/Speichern

### Greedy
Baue Lösung aus Folge lokal bester Auswahlen zusammen
siehe Kruskal,Prim,Dijkstra

### Metaheuristiken
Übergeordnete Methoden für Optimierungsprobleme

## Backtracking

## Prinzip 
Finde Lösungen $x=(x_{1},x_{2},\dots x_{n})$ oder "Trial and Error", indem Teillösung $x_{1},x_{2},\dots x_{i-1})$ durch Kandidaten $x_{i}$ ergänzt wird, bis Gesamtlösung erhalten, oder bis fesregestellt wird, dass keine Gesamtlösung erreichbar und Kandidat $x_{i-1}$ revidiert wird

## Beispiel: 4x4 Sudoku
`SUDOKU-BACKTRACKING(B)//B[0...3][0...3] board`
```java
IF isFull(B) THEN //prüft, ob Board ausgefüllt ist
	print "solution: " +B;
ELSE
	(i,j) = nextFreePos(B);//nächste freie Position
	FOR v=1 TO 4 DO
		IF isAdmissible(B,i,j,v) THEN //prüft Kriterien oben
		B[i,j]=v;
		SUDOKU-BACKTRACKING(B);
	B[i,j] =empty //Löscht Feld vor Rückkehr
```

## Lösungssuche 
1. Finde eine Lösung
2. Finde alle Lösungen
3. Finde beste Lösung

## Backtracking vs
Backtracking vs DFS: Backtracking kann als Tiefensuche auf Rekursionsbaum betrachten, wobei aussichtslose Lösungen evtl frühzeitig abgeschnitten werden

Backtracking vs Brute-Force-Search: Backtracking "intelligenter", da aussichtslose Lösungen aussortiert werden

## Beipiel: Regulärer Ausrduck
![[Pasted image 20240730192811.png]]


## Dynamische Programmierung
- Teile Problem in (überlappende) Teilprobleme
- Löse rekursiv Teilprobleme, verwende dabei Zwischenergebnisse wieder(Memoization) 
- Rekonstruiere Gesamtlösung
- Schwierigkeit: Finden geeigneter Rekursionen

### Beispiel: Fibonacci
`Fib-Rek(n)`
```JAVA
if N=<2 THEN
	return 1;
ELSE
	return Fib-Rek(n-1) + Fib-Rek(n-2);
```


## Fibonacci mit Memoization

`FibDyn(n)`
```java
F[]=ALLOC(n); //F_i at F[i-1]
FOR i=0 TO n-1 DO F[i]=0;
return FibDynRek(n-1,F);
```
`FibDynRek(i,F)`
```java
IF F[i] != 0 THEN return F[i] //already calculated
IF i=<1 THEN
	f=1
ELSE
	f=FibDynRek(i-1,F)+FibDynRek(i-2,F);
F[i]=f;
return f;
```
![[Pasted image 20240802183244.png]]
 Laufzeit $\theta(n)$
 ![[Pasted image 20240802183343.png]]
 Wenn Basisfall erreicht ist, nur noch Addieren und Auslesen

## Minimum Edit Distance/Levenshtein-Distanz

Ziel:
- Messen der Ähnlichkeit von Texten
- Definiere 3 Buchstabenoperationen:
	 1.`ins(S,i,b)`: fügt an `i`-ter Postion Buchstabe `b` in String `S` ein
	 2.`del(S,i)` : löscht an `i`-ter Postion Buchstaben in `S`
	 3. `sub(S,i,b)`: ersetzt an `i`-ter Postion in S den Buchstaben durch `b`
- Messe Äähnlichkeit, von Texten: wie viele (Buchstaben-) Operationen
- Nutze noch `copy(S,i)` für das Kopieren des `i`-ten Buchstabens, Kosten: 0 Algorithmische Sichtweise:
String `X[1..m]` von links nach rechts in String `Y[1..n]` überführen
Zu jedem Zeitpunkt ist `X[1...i]` bereits in `Y[1...j]` transformiert
`D[i][j]` sei Distanz, um `X[1..i]` bereits in `Y[1..j]` zu überführen
Betrachte nun nächsten Schritt um `X` in `Y` zu überführen:
- `copy: D[i][j]=D[i-1][j-1]
	Bereits `X[1..i-1]` in `Y[1..j-1]` überführt, jetzt kostenfrei kopieren
- `sub : D[i][j] = D[i-1][j-1] + 1` Bereits `X[1..i-1] in Y[1..j-1]` überführt, jetzt ersetzen
- `del : D[i][j] = D[i-1][j] + 1 Bereits X[1..i-1]` in `Y[1..j]` überführt, jetzt `X[i]` löschen
- `ins : D[i][j] = D[i][j-1] +1`  Bereits `X[1..i]` in `Y[1..j-1]` überführt, jetzt `Y[j]` einfügen Fasse copy und sub zusammen:
- `copy/sub : D[i][j] = D[i-1][j-1] + (X[i] != Y[j])` (Ausdruck ist 1 wenn wahr, sonst 0) Suche nach der besten Strategie ist nun: `D[i][j] = min {D[i-1][j-1] + (X[i] != Y[j]), D[i-1][j] + 1, D[i][j-1] + 1}`
- Es gilt noch folgendes für Ränder:
	- `D[0][j] = j` : Füge `j` Buchstaben `Y[1..j]` zu leerem String `X[1..0]` hinzu
	- `D[i][0]=i:` Lösche `i` Buchstaben `X[1...i]` um leeren String `Y[1...0]` zu erhalten

### Algorithmus
verwendet dynamische Programmierung und Memoization

`MinEditDist(X,Y,m,n) // X=X[1..m],Y=Y[1..n]`
```java
D[][]= ALLOC(m,n);
FOR i=0 TO m DO D[i][0]=i;
FOR j=0 TO n DO D[0][j]=j;
FOR i=1 to M DO
	FOR j=1 TO n DO
		IF X[i]=Y[j] THEN s=0 ELSE s=1;
		D[i][j]=min{D[i-1][j-1]+a,D[i-1][j]+1,D[i][j-1]+1};
return D[m][n];
```
![[Pasted image 20240802190036.png]]
![[Pasted image 20240802190048.png]]
![[Pasted image 20240802190142.png]]



## Greedy-Algorithmen

## Prinzip
Finde Lösung $x=(x_{1},x_{2},\dots x_{n})$ in dem Teillösung $(x_{1},x_{2},x_{i-1})$ durch den Kandidaten $x_{i}$ ergänzt wird, der lokal am günstigsten erscheint

### Beispiele
- Dijksta: Wähle immer Knoten, der die kürzeste Distanz hat
- Kruskal: Wähle jeweils leichteste Kante
Greedy-Algorithmen funktionieren oft, aber nicht immer (z.B: Dijkstra und negative Kantengewichte)

## Traveling Salesperson Problem(TSP):
Gegeben vollständiger (un-)gerichteter Graph $G=(V,E)$ mit Kantengewichten $w:E\to \mathbb{R}$, finde Tour $p$ mit minimalem Kantengewicht $w(p)$.
Eine Tour ist ein Weg $p=(v_{0},v_{1},\dots,v_{n})$ entlang der Kanten $(v_{i},v_{i+1}) \in E$ für $i=0,1,2\dots, n-1$ der bis auf Start und Endknoten $v_{0}=v_{n}$
jeden Knoten genau einmal besucht $(V=\{ v_{0},v_{1},v_{n-1} \})$
Graph $G=(V,E)$ ist vollständig, wenn es für alle $u,v \in V, u\neq v$ eine Kante $(u,v)\in E$ gibt.
Unvollständiger Graph mit Tour lässt sich erweitern, indem man fehlende Kanten $(u,v)$ verboten teuer macht: $w((u,v)):=|V|\cdot max_{e\in E}\{ |w(e)| \}+1$ für alle $(u,v)\\\not\in E$

### TSP vs. Dijkstra
- Allgemeiner TSP-Algortihmus:
	- Finde optimale Route, die durch jeden Knoten geht und zum Ausgangspunkt zurückkehrt
- Dijkstra löst anderes Problem:
	- Finde optimalen Pfad vom Ausgangspunkt aus
	- Besucht eventuell nicht alle Knoten und betrachtet auch nicht Rückkehr

### Ansatz Greedy-Algorithmus für TSP
Starte mit beliebigem oder gegebenem Knoten.
Nehme vom gegenwärtigen Knoten aus die Kante zu noch nicht besuchtem Knoten, die kleinstes Gewicht hat.
Wenn kein Knoten mehr übrig, gehe zu Startpunkt zurück.

`Greedy-TSP(G,s,w) // |V|=n, s starting node`
```Java
FOREACH v in V DO v.color=white;
tour[]=ALLOC[n]; tour[0]=s; tour[0].color=gray;
FOR i=1 TO n-1 DO
	tour[i]=EXTRACT-MIN(adj(tour[i-1]));
	// get (white) neighbour with minimum edge weight
	tour[i].color=gray;
return tour;
```
![[Pasted image 20240802192836.png]]

# Metaheuristiken

## Heuristik
- Dedizierter Suchalgorithmus für Optimierungsproblem, der gute (eventuell nicht optimale) Lösung für spezielles Problem findet
- Problem-abhängig:Arbeitet mit konkretem Problem

## Metaheuristik
- Allgemeine Vorgehensweise, um Suche für beliebige Optimierungsprobleme zu leiten
- Problem-unabhängig: Arbeitet mit abstrakten Problemen

## Lokale Suche/Hill-Climbing-Strategie

1. Finde erste Lösung
2. Suche in Nähe bessere Lösungen, bis keine Verbesserung mehr/ Zeit um

### Hill-Climbing-Algorithmus

`HillClimbing(P) // maxTime constant`
```java
sol=initialSol(P); // wähle initiale Lösung
time = 0;
WHILE time<maxTime DO
	new = perturb(P,sol); // ändere Lösung leicht ab
	IF quality(P,new) > quality(P,sol) THEN
		sol=new; // eretze aktuelle Lösung durch neu, falls diese besser ist
	time=time+1;
return sol;
```

### Beispiel TSP
- `initSol`: Wähle beliebige Tour, z.B per Greedy-Algorithmus
- `perturb`: Tausche 2 zufällige Knoten
- `quality`: Gewicht der aktuellen Tour

### Lokale vs. globale Maxima

![[Pasted image 20240802193807.png]]
![[Pasted image 20240802193836.png]]
![[Pasted image 20240802193906.png]]

## Simulated Annealing

- "Annealing" in Metallverarbeitung:
	Härten von Metallen durch erhitzen auf hohe Temperatur und langsames Abkühlen
- Entscheide je nach Temperatur, in welche Richtung gesucht wird
1. Temperatur zu Beginn hoch, kühlt langsam ab
2. Je höher Temperatur, desto wahrscheinlicher Sprung in schlechte Richtung

- Mit Wahrscheinlichkeit in schlechte Richtung

### Ansatz
Akzeptiere auch Lösung `new` mit `quality(new)<quality(sol)`  mit Wahrscheinlichkeit:
$rand(0,1)<e^\frac{quality(new)-qualit(sol)}{temperature}$ $temperature$ nimmt die Zeit ab
- Zu Beginn heiße Temperatur: Akzeptiere oft viel schlechtere Lösungen
- Am Ende kühlere Temperatur: Akzeptiere selbst wenig schlechtere Lösungen fast nie gegen Ende fast Hill-Climbing-Strategie

![[Pasted image 20240802194925.png]]


## Weitere Metaheuristiken

### Tabu Search
- Suche bessere Lösung in der Nähe ausgehend von aktueller Lösung
- Speichere eine Zeit lang schon besuchte Lösungen, vermeide diese Lösungen
- Wenn keine bessere Lösung in der Nähe, akzeptiere auch schlechtere Lösung

### Evolutionäre Algorithmen

- Beginne mit Lösungspopulation
- Wähle beste Lösung zur Reproduktion aus
- Bilde durch Überkreuzungen und Mutationen der besten Lösungen neue Lösungen
- Ersetze schlechteste Lösungen durch diese neue Lösungen

