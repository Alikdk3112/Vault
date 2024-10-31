# Binary Heap Trees
## Definition:
- bis auf das unterste Level vollständig und im untersten Level von links gefpllt
- für alle knoten gilt : `x.parent.key >= x.key`
- *Keine BST,* links kann größer sein als rechts
- Bei Min-Heaps sind die Werte in Elternknoten  jeweils kleiner

### Eigenschaften:
-  Es gilt, $h \leq \log n$
- Maximum = Wurzel

## Heaps durch Arrays
-  Anzahl der Knoten werden in `H.length` gespeichert
- Duale Sichtweise als Pointer  oder als Array (j ist Index von Array)
	- j.parent = $\frac{j}{2} -1$
	- j.left = $2(j+1) -1$
	- j.right = $2(j + 1)$
![[Pasted image 20240617183514.png|400]]
## Einfügen 

~ Position durch Baumstruktur vorgegeben
~ Vertausche nach oben, bis Max Eigenschaft wieder erfüllt ist

```java
insert(H,k) // als unbeschränktes Array
	H.length = H.length + 1;
	H.A[H.length - 1] = k; // wert wird links hinzugefügt
	i = H.length-1;
	WHILE i>0 AND H.A[i] > H.A[i.parent]
		SWAP(H.A,i,i.parent) // bis k < parent, swappen
		i = i.parent
```
 
Laufzeit : $O(h) = O(\log n)$

## Lösche Maximum

1.Ersetze Maximum durch "letztes" Blatt
2. Stelle Max Eigenschaften wieder her, indem Knoten nach unten gegen das Maximum der beiden Kinder getauscht wird (`heapify`)
`extract-max(H)`
```java
IF isEmpty(H) THEN
	return error "underflow"
ELSE 
	max = H.A[0];
	H.A[0] = H.A[H.length - 1];
	H.Length = H.length - 1;
	heapify(H,0);
	return max;
```

`heapify(H,i)`
```java
maxind = i;
IF i.left<H.length AND H.A[i]<H.A[i.left] THEN
	maxind =i.left;
IF I.right<H.length AND H.A[maxind]<H.A[i.right] THEN
	maxind=i.right;

IF maxind != i THEN
	SWAP(H.A,i,maxind)
	heapify(H,maxind)
```

## Heap Konstruktion aus Array
- Blätter sind für sich triviale Max-Heaps
- Bauen von Max Heaps für Teilbäume mithilfe Rekursion per heapify
- (Array nicht unbeding in richtiger Reihenfolge)

`buildHeap(H) // Array schon nach H.A kopiert`
```java
H.length=A.length;
FOR i = ceil((H.length-1/2) -1) DOWN TO 0 DO // ceil = floor
	heapify(H,i);
```
![[Pasted image 20240617192025.png]]
![[Pasted image 20240617192106.png|300]]
Blätter werden sortiert, bis heap enstehen kann

## Heap-Sort

Gibt Einträge in Array A in absteigender größe aus
der Maximale Wert wird ausgegeben und gelöscht
`heapSort(H) // Array schon nach H.A kopiert`
```java
buildHeap(H); // Bauen des Heaps
WHILE !isEmpty do PRINT extraxt-max(H); // Ausgabe des Maximums bis Heap leer ist
```

## Abstrakter Datentyp Priority Queue
- ´`new(Q)` erzeugt neue, leere priority Queue namens q
- `isEmpty(Q)` gibt an, ob Queue Q leer ist
- `max(Q)` gibt größtes Element aus Queue Q zurück
- `extract-max(Q)` gibt größtes Element aus Queue zurück und löscht es aus Q
- `insert(Q,k)` fügt Wert k zu Queue hinzu, implementation kann priority Heap verwenden

---
# B-Bäume
## Definition:
- bis auf das unterste Level vollständig und im untersten Level von links gefpllt
- für alle knoten gilt : `x.parent.key >= x.key`
- *Keine BST,* links kann größer sein als rechts
- Bei Min-Heaps sind die Werte in Elternknoten  jeweils kleiner

### Eigenschaften:
-  Es gilt, $h \leq \log n$
- Maximum = Wurzel

### Heaps durch Arrays
-  Anzahl der Knoten werden in `H.length` gespeichert
- Duale Sichtweise als Pointer  oder als Array (j ist Index von Array)
	- j.parent = $\frac{j}{2} -1$
	- j.left = $2(j+1) -1$
	- j.right = $2(j + 1)$
![[Pasted image 20240617183514.png|400]]
## Einfügen 

~ Position durch Baumstruktur vorgegeben
~ Vertausche nach oben, bis Max Eigenschaft wieder erfüllt ist

```java
insert(H,k) // als unbeschränktes Array
	H.length = H.length + 1;
	H.A[H.length - 1] = k; // wert wird links hinzugefügt
	i = H.length-1;
	WHILE i>0 AND H.A[i] > H.A[i.parent]
		SWAP(H.A,i,i.parent) // bis k < parent, swappen
		i = i.parent
```
 
Laufzeit : $O(h) = O(\log n)$

### Lösche Maximum

1.Ersetze Maximum durch "letztes" Blatt
2. Stelle Max Eigenschaften wieder her, indem Knoten nach unten gegen das Maximum der beiden Kinder getauscht wird (`heapify`)
`extract-max(H)`
```java
IF isEmpty(H) THEN
	return error "underflow"
ELSE 
	max = H.A[0];
	H.A[0] = H.A[H.length - 1];
	H.Length = H.length - 1;
	heapify(H,0);
	return max;
```

`heapify(H,i)`
```java
maxind = i;
IF i.left<H.length AND H.A[i]<H.A[i.left] THEN
	maxind =i.left;
IF I.right<H.length AND H.A[maxind]<H.A[i.right] THEN
	maxind=i.right;

IF maxind != i THEN
	SWAP(H.A,i,maxind)
	heapify(H,maxind)
```

## Heap Konstruktion aus Array
- Blätter sind für sich triviale Max-Heaps
- Bauen von Max Heaps für Teilbäume mithilfe Rekursion per heapify
- (Array nicht unbeding in richtiger Reihenfolge)

`buildHeap(H) // Array schon nach H.A kopiert`
```java
H.length=A.length;
FOR i = ceil((H.length-1/2) -1) DOWN TO 0 DO // ceil = floor
	heapify(H,i);
```
![[Pasted image 20240617192025.png]]
![[Pasted image 20240617192106.png|300]]
Blätter werden sortiert, bis heap enstehen kann

### Heap-Sort

Gibt Einträge in Array A in absteigender größe aus
der Maximale Wert wird ausgegeben und gelöscht
`heapSort(H) // Array schon nach H.A kopiert`
```java
buildHeap(H); // Bauen des Heaps
WHILE !isEmpty do PRINT extraxt-max(H); // Ausgabe des Maximums bis Heap leer ist
```

## Abstrakter Datentyp Priority Queue
- ´`new(Q)` erzeugt neue, leere priority Queue namens q
- `isEmpty(Q)` gibt an, ob Queue Q leer ist
- `max(Q)` gibt größtes Element aus Queue Q zurück
- `extract-max(Q)` gibt größtes Element aus Queue zurück und löscht es aus Q
- `insert(Q,k)` fügt Wert k zu Queue hinzu, implementation kann priority Heap verwenden

---## Randomized Data Structures
-  Deterministische Datenstrukturen
-bisher war alles deterministsich, Verhalten für identische Eingaben immer gleih
- Randomisierte Datenstrukturen
-nun hängt Verhalten auch von zufälligen Entscheidungen der Datenstruktur ab

## Skip Lists
- Zweidimensionale Datenstruktur 
- Füge rekursiv **Express-Listen** ein
- Diese haben weniger Elemente als die ursprüngliche Liste

### Suche mittels Express-Listen
Beginne in Express-Liste:
-  Wenn Element gefunden, dann ausgeben
- Wenn nächstes Element $\leq$ gesuchtem Element, weiter nach rechts
- Wenn nächstes Element in Express-Liste größer als gesuchtes Element, nach unten

![[Pasted image 20240624171006.png]]
## Implementierung
- `L.head` - erstes/oberstes Element der Liste
- `L.height` - Höhe der Skiplist
- `x.key`-Wert
- `x.next/x.previous` - Nachfolger/Vorgänger
- `x.down`- Nachfolger Liste unten
- `x.up` - Nachfolger Liste oben
- `nil` - kein Nachfolger/leeres Element

## Suchalgorithmus
`search(L,k)`
```java
current = L.head;
WHILE current != DO
	IF current.key == k THEN return current;
	IF current.next != nil AND 
	current.next.key <= k

	THEN current = current.next
	ELSE current = current.down;
return nil;
```
Laufzeit hängt von Expresslisten ab

### Auswahl der Elemente für Express-Listen

wähle jedes Element aus Liste mit Wahrscheinlichkeit $p$ (z.B. $p = \frac{1}{2}$) für übergeordnete Liste.
--> die Wahrscheinlichkeit, ob ein Element in die übergeordnete Liste versetzt wird beträgt $\frac{1}{2}$ & es ist zufällig
Durschnittliche Höhe $h\in 0\left( \log_{\frac{1}{p}} n\right)$

![[Pasted image 20240624174721.png]]

### Laufzeit für Suchen
Im schlimmsten Fall wird Suche erst in unterster Liste beendet
Wenn Skip-Liste Höhe $h$, braucht man im Durschnitt$\frac{h}{p}\in O(h) = O(\log n)$ viele Schritte
--> Durschnittliche Laufzeit = O(h)

### Einfügen
- Füge auf unterster Ebene ein und dann eventuell auf Ebenen darüber
- Zufällige Wahl mit Wahrscheinlichkeit $p$ auf jeder Ebene 

--> Durchnilliche Laufzeit = $O(h)$
![[Pasted image 20240624175825.png]]
**Vorgehen**
	1. Skip-Liste durch gehen und schauen, wo $a\leq x\leq b$ gilt:
	2. $x$ wird eingefügt und es wird per Zufall (Bsp: $p=\frac{1}{2}$) bestimmt, ob $x$ eine höher platziert wird 
	3. Wenn ja, mssen stehts die neuen Vor & Nachgänger initialisiert werden
• falls ein Element nicht auf die nächst höhere Ebene gelangt, gelangt es auch nicht auf andere höhere Ebenen (Abbruch des Auswahlprozesses)

### Löschen
-  Element wird auf allen Ebenen gelöscht, (Vor & Nachgänger weisen nicht mehr darauf)
--> Durschnittliche Laufzeit = $O(h)$
##### Laufzeiten
![[Pasted image 20240624180645.png]]
##### Speicherbedarf
-  Im Durschnitt: $\frac{n}{1-p}$
### Anwendung
Einfügen/Löschen unterstützen parallele Verarbeitung (z.B. Multi-Core-Systeme), da nur sehr lokale Änderungen
Bäume mit Re-Balancierung können dies nicht
--> Dafür logarithmische Laufzeit im Durschnitt

---

## Randomized Data Structures
-  Deterministische Datenstrukturen
-bisher war alles deterministsich, Verhalten für identische Eingaben immer gleih
- Randomisierte Datenstrukturen
-nun hängt Verhalten auch von zufälligen Entscheidungen der Datenstruktur ab

## Skip Lists
- Zweidimensionale Datenstruktur 
- Füge rekursiv **Express-Listen** ein
- Diese haben weniger Elemente als die ursprüngliche Liste

### Suche mittels Express-Listen
Beginne in Express-Liste:
-  Wenn Element gefunden, dann ausgeben
- Wenn nächstes Element $\leq$ gesuchtem Element, weiter nach rechts
- Wenn nächstes Element in Express-Liste größer als gesuchtes Element, nach unten

![[Pasted image 20240624171006.png]]
## Implementierung
- `L.head` - erstes/oberstes Element der Liste
- `L.height` - Höhe der Skiplist
- `x.key`-Wert
- `x.next/x.previous` - Nachfolger/Vorgänger
- `x.down`- Nachfolger Liste unten
- `x.up` - Nachfolger Liste oben
- `nil` - kein Nachfolger/leeres Element

## Suchalgorithmus
`search(L,k)`
```java
current = L.head;
WHILE current != DO
	IF current.key == k THEN return current;
	IF current.next != nil AND 
	current.next.key <= k

	THEN current = current.next
	ELSE current = current.down;
return nil;
```
Laufzeit hängt von Expresslisten ab

### Auswahl der Elemente für Express-Listen

wähle jedes Element aus Liste mit Wahrscheinlichkeit $p$ (z.B. $p = \frac{1}{2}$) für übergeordnete Liste.
--> die Wahrscheinlichkeit, ob ein Element in die übergeordnete Liste versetzt wird beträgt $\frac{1}{2}$ & es ist zufällig
Durschnittliche Höhe $h\in 0\left( \log_{\frac{1}{p}} n\right)$

![[Pasted image 20240624174721.png]]

### Laufzeit für Suchen
Im schlimmsten Fall wird Suche erst in unterster Liste beendet
Wenn Skip-Liste Höhe $h$, braucht man im Durschnitt$\frac{h}{p}\in O(h) = O(\log n)$ viele Schritte
--> Durschnittliche Laufzeit = O(h)

### Einfügen
- Füge auf unterster Ebene ein und dann eventuell auf Ebenen darüber
- Zufällige Wahl mit Wahrscheinlichkeit $p$ auf jeder Ebene 

--> Durchnilliche Laufzeit = $O(h)$
![[Pasted image 20240624175825.png]]
**Vorgehen**
	1. Skip-Liste durch gehen und schauen, wo $a\leq x\leq b$ gilt:
	2. $x$ wird eingefügt und es wird per Zufall (Bsp: $p=\frac{1}{2}$) bestimmt, ob $x$ eine höher platziert wird 
	3. Wenn ja, mssen stehts die neuen Vor & Nachgänger initialisiert werden
• falls ein Element nicht auf die nächst höhere Ebene gelangt, gelangt es auch nicht auf andere höhere Ebenen (Abbruch des Auswahlprozesses)

### Löschen
-  Element wird auf allen Ebenen gelöscht, (Vor & Nachgänger weisen nicht mehr darauf)
--> Durschnittliche Laufzeit = $O(h)$
##### Laufzeiten
![[Pasted image 20240624180645.png]]
##### Speicherbedarf
-  Im Durschnitt: $\frac{n}{1-p}$
### Anwendung
Einfügen/Löschen unterstützen parallele Verarbeitung (z.B. Multi-Core-Systeme), da nur sehr lokale Änderungen
Bäume mit Re-Balancierung können dies nicht
--> Dafür logarithmische Laufzeit im Durschnitt

---

# Hash Tables
## Idee
- h: Datenmenge $-->$ $[0,T.length-1]$ ist uniform und unabhängig verteilt, **Hashfunktion** h = mathematische Funktion
![[Pasted image 20240624182520.png]]
  **Suche**: ist `x` in `T[h(x)]` vorhanden ?
  **Löschen:** Lösche `x` aus `T[h(x)]`
  ![[Pasted image 20240624182740.png]]

### Kollisionsauflösung
-  Wenn Array-Eintrag schon belegt, bilde verkette Liste und füge neues Element vorne ein
- sei $y$ belegter Eintrag und $x$ das einfügende Element, dann: ![[Pasted image 20240624184624.png]]

### Hash Tables mit verketteten Listen
- Einfügen immernoch konstante Anzahl Array-/Listen-Operationen
- Suchen/Löschen benötigen so viele Schritte, wie jeweilige Liste lang ist
- Wenn Hashfunktion uniform verteilt, dann hat jede Liste im Erwartungswert $\frac{n}{T.length}$ viele Einträge

##### Laufzeit
- Bei uniform und unabhängig verteilten Hashwerten benötigt **Suchen** und **Löschen** im Durschnitt $\Theta\left( \frac{n}{T.length} \right)$ viele Schritte
- **Einfügen**: $\Theta(1)$
--> Wählt man $T.length\approx n$, ergibt sich konstante Laufzeit im Durschnitt

## Gute Hash-Funktionen

#### "Universelle" Hash-Funktion
-  Interpretiere (Binär-)Daten als Zahlen zwischen $0$ UND $p-1$. $p$ ist prim, $p> > T.length$
- wähle zufällige $a,b \in [0,p-1],$ $a\neq 0$ setze $((a\cdot x + b))\text{ mod } p) \text{ mod } T.length$
- Verteilung und Unabhängigkeit/Kollisionsresistenz gewährleistet
![[Pasted image 20240624192105.png]]

Wird zum Beispiel MySQL verwendet
### Hash Tables vs Bäume

| Hash Tablee                                                     | Baum                                                                         |
| --------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Nur Suche nach bestimmten Wert möglich                          | Schnelles Traversieren möglich(z.B nächstkleinerer Wert, auch Bereichssuche) |
| In der Regel Hashtable größer als zu erwartende Anzahl Einträge |                                                                              |
#### Laufzeiten Speicher 
**Einfügen:** $\Theta(1)$ im Worst-Case
**Löschen:** $\Theta(1)$ im Durschnitt
**Suchen** $\Theta(1)$ im Durschnitt
Speicherbedarf größer in der Regel als $n$ , üblicherweise ca. $1,33 * n$

---


#### "Universelle" Hash-Funktion
-  Interpretiere (Binär-)Daten als Zahlen zwischen $0$ UND $p-1$. $p$ ist prim, $p> > T.length$
- wähle zufällige $a,b \in [0,p-1],$ $a\neq 0$ setze $((a\cdot x + b))\text{ mod } p) \text{ mod } T.length$
- Verteilung und Unabhängigkeit/Kollisionsresistenz gewährleistet
![[Pasted image 20240624192105.png]]

Wird zum Beispiel MySQL verwendet
### Hash Tables vs Bäume

| Hash Tablee                                                     | Baum                                                                         |
| --------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Nur Suche nach bestimmten Wert möglich                          | Schnelles Traversieren möglich(z.B nächstkleinerer Wert, auch Bereichssuche) |
| In der Regel Hashtable größer als zu erwartende Anzahl Einträge |                                                                              |
#### Laufzeiten Speicher 
**Einfügen:** $\Theta(1)$ im Worst-Case
**Löschen:** $\Theta(1)$ im Durschnitt
**Suchen** $\Theta(1)$ im Durschnitt
Speicherbedarf größer in der Regel als $n$ , üblicherweise ca. $1,33 * n$

---

# Graphen
## Endlich gerichtete Graphen
 besteht aus  
 1. endliche Knotenmenge $V$ ("vertices)
 2. Endliche Kantenmenge $E \subseteq V\times V\;(u,v)\in E$: Kante von Knoten $u$ zu $v$ ("edges")
 ![[Pasted image 20240626173031.png]]
 - **Stark Zusammenhängend**, wenn jeder Knoten gemäß Kantenrichtung erreichbar ist
## Ungerichtete Graph
-  Endlicher Graph, aber $(u,v) \in E\iff (u,v)\in E$
- Alternative Darstellung ${u,v}$
![[Pasted image 20240626173721.png]]
## Pfadfinder
Knoten $v$ ist von Knoten$u$ im Graphen $G=(V,E)$ erreichbar, wenn es Pfad $(w_{1},\dots,w_{k}) \in V^k$ gibt, sodass $(w_{i}),w_{i+1}\in E$ für $i = 1,2,\dots,k-1, w_{1}=u,w_{k}=v$
$-\to$ Formal für, wann ein Knoten erreichbar ist
$(w_{1},\dots,w_{k})$ ist kürzester Pfad, wenn es keinen kürzeren Pfad gibt
$shortest(u,v):=$ Länge eines kürzesten Pfades von $u$ nach $v$, kürzester Pfad muss nicht eindeutig sein

## Graphen und Bäume
Graphenbäume haben keine Ordnung auf Kindern
$G$ ist ein Baum, wenn $V$ leer ist oder es ein $r\in V$(Wurzel)
gibt, sodass jeder Knoten $v$ von $r$ per eindeutigem Pfad erreichbar ist

## Subgraphen 
$G^{'}$ Muss wieder ein Graph gleichen Typs (gerichtet/ungerichtet) sein. Graph $G^{'}= (V^{'},E^{'})$
ist Subgraph von $G=(V,E)$, wenn $V{'}\subseteq V \}$
und $E{'}\subseteq E$
![[Pasted image 20240626183633.png]]

## Darstellung von Graphen
### Adjazenmatrix
$i$ Zeile, $j$ Spalte
$$A[i,j]=
\begin{cases}
1 &\text{wenn Kante von i zu j}  \\
0& \text{sonst}
\end{cases}$$
![[Pasted image 20240626184647.png]]
- Bei ungerichteten Graphen ist Matrix (spiegel-)symetrisch zur Hauptdiagonalen
- Speicherbedarf $=\theta(|V^2|)$
- $a^{(m)}_{i,j}$ der m-ten Potenz $A^m$ der **Adjazentenmatrix** $A$ eines Graphen gibt die Anzahl der Wege an, die von Knoten $i$ zu $j$ entlang genau $m$ Kanten führen

### Adjazenzliste
Array mit verketten Listen (sortiert/unsortiert)
Speicherbedarf $=\theta(|V|+|E|)$
![[Pasted image 20240626191311.png]]
Alle Nachbarn werden sozusagen verkettet, wenn die Kante in die Richtung zeigt

## Gewichtete Graphen
- Besitzt zufällige Funktion $w:E->\mathbb{R}$
- Ungerichtete, gewichtete Graphen: $w((u,v))=w((v,u))$ für alle $(v,u)\in E$
- Wert $w((u,v))$ wird abgespeichert
![[Pasted image 20240626192431.png]]

## Breitensuche/Breadth-First Search (BFS)
Besuche zuerst unmittelbare Nachbarn, dann deren Nachbarn usw

## Algorithmus

`BFS(G,s)//G=(V(Knotenmenge),E(Kantenmenge)), s=source node in V, Startknoten` 
```java
FOREACH u in V-{s} DO
	u.color=WHITE; //Alle Knoten werden als nicht besucht markiert
	u.dist=+unendlich; //Distanz von s zu allen anderen Knoten wird auf unendlich gesetzt
	u.pred = NIL;//Vorgänger des Startknotens ist NIL
s.color=GRAY;// Der Startknoten wird als besucht aber nicht erforscht markiert
s.dist=0;//Distanz von s zu sich selber auf 0 setzen
s.pred=NIL;// Vorgänger von s ist NIL
// Erstelle eine neue leere Warteschlange
newQueue(Q);
enqueue(Q,s); // Füge den Startknoten in Warteschlange
WHILE !isEmpty(Q) DO
	u=dequeue(Q); // entferne das vorderste Elemen aus der Warteschlange
	
	FOREACH v in adj(G,u) DO // gehe alle benachbarten Knoten von u
		IF v.color==WHITE THEN // wenn noch nicht besucht
			v.color=GRAY; // Markiere als besucht
			v.dist=u.dist+1; //setze die Distanz des benachbarten Knoten auf die Distanz von u +1
			v.pred=u; // u als Vorgänger von v
			enqueue(Q,v); // füge benachbarten Knoten in Warteschlange ein
	u.color=BLACK; // u ist vollständig erforscht
```
- `adj(G,u)` = Liste aller Knoten $v \in E$ (Reihenfolge irrelevant)

## Kürzeste Pfade ausgeben


`PRINT-PATH(G,s,v)// assumes that BFS(G,s) has already been executed`
```Java
IF v==s THEN
	print s
ELSE 
	IF v.pred==NIL THEN
		PRINT "no path from s to v"
	ELSE
		PRINT-PATH(G,s,v.pred);
		PRINT v;
```
Laufzeit ohne BFS $=O(|V|)$

## Abgeleiteter BFS-Baum

Definiere Subgraph $G^{s}_{pred}:=V^{s}_{pred},E^{s}_{pred}$ von G durch:
- $V^{s}_{pred}:=\{ v\in V:v.pred \neq NIL \} \cup \{ s \}$
- $E^{s}_{pred}:=\{ (v.pred,v): v\in(V^{s}_{pred}\setminus \{  s\} )\}$ und $(v,v.pred)$ für ungerichtete Graphen $G^{s}_{pred}$ ist BFS-Baum zu $G$:
- ![[Pasted image 20240728135909.png]]
## Tiefensuche/Depth-First Search (DFS)
**Prinzip:**
Das Prinzip des Depth-First Search Algorithmus ist, dass im Gegensatz zu BFS nicht erst alle Nachbarn eines Knotens besucht werden, sondern immer erst ein Pfad zuende gebracht wird, bevor ein anderer besucht wird. Der Algorithmus geht also solange einen Pfad ab, bis er an einem Knoten keine neuen Knoten mehr findet, wodurch er dann einen Knoten zurück geht und von diesem den nächsten Pfad abgeht. Dies macht er solange, bis er alle Pfade abgelaufen ist. Allgemein kann man als Unterschied zu BFS sagen, dass dieser Algorithmus mehr der Stack Datenstruktur ähnelt, da sie zuerst die Knoten merkt und dann den zuletzt hinzugefügten Knoten verarbeitet.

`DFS(G)//G=(V,E)`
```JAVA
FOREACH u in V DO
	u.color=WHITE;
	u.pred=NIL;
time=0;
FOREACH u in V DO
	IF u.color==WHITE THEN
		DFS-VISIT(G,u)
		
```
`DFS-VISIT(G,u)`
```java
time=time+1;
u.disc=time;
u.color=GRAY;
FOREACH v in adj(G,u) DO
	IF v.color==WHITE THEN
		v.pred=u;
		DFS-VISIT(G,v);
u.color=BLACK;
time=time+1;
u.finish=time;
```
- `time`: globale Variable
- `disc`: discovery time
- `finish`: finish time
Laufzeit $=O(|V|+|E|)$
Standardordnung der Knoten ist gemäß der Nummer


![[Pasted image 20240728140746.png]]

## DFS-Wald = Menge von DFS-Bäumen
$E_{pred}=\{( v.pred,v)|v\in V,v.pred\neq NIL \}$ und $(v,v.pred)$ für ungerichtete Graphen
![[Pasted image 20240728141005.png]]


### Kantenart erkennen
Sei $(u,v)$ gerade betrachtete Kante in DFS-Algorithmus. Dann ist (u,v)...
eine Baumkante, wenn `´v.color==WHITE`
eine Rückwärtskante,wenn `v.color==GRAY`
eine Vorwärtskante, wenn `V.color==BLACK` und `u.disc<v.disc`
eine Vorwärtskante, wenn `V.color==BLACK` und `u.disc>v.disc`

--> In ungerichteten Graphen entstehen nur Baum und Rückwärtskanten


### DFS Anwendungen

## Abstrakte Modellierung: Toplogische Sortierung

- Nur für "DAG"(directet acyclic graph)--> Gerichteter Graph ohne Zyklen 
- Sortiere Knoten in linearer Ordnung, so dass für alle Knoten $u,v \in V$ gilt, dass $u$ vor $v$ in der Ordnund kommt, wenn $(u,v) \in E$
- Kanten gehen nur nach rechts
- Sortierung muss nicht eindeutig sein

### Beispiel:
![[Pasted image 20240728142321.png]]
führt zu:
![[Pasted image 20240728142347.png]]

`TOPOLOGICAL-SORT(G)//G=(V,E) dag`
```java
newLinkedList(L);
run DFS(G) but, each time a node is finished, insert in front of L
return L.head
```
Laufzeit$= O(|V|+|E|)$; Da einfügen in Liste vorne in Zeit $O(1)$

Wenn Anzahl eingehender Kanten bekannt ist:
`Kahn1962 (G) //G=(V,E) dag, inbound[u] = #edges to u`
```JAVA
WHILE !isEmpty(V) DO
	pick vertes u with inbound[u] ==0
	add u at the end of a list L
	inbound[v]=inbound[v]-1 for each v with (u,v) in E
	remove u from V and all (u,*) from E
```

## Starke Zusammenhangskomponenten (strongly connected components, SCCs)

Ein Graph heißt zusammenhängend, wenn 

Eine starke Zusammenhangskomponente eines gerichteten Graphen $G=(V,E)$ ist eine Knotenmenge $C \subseteq V$, sodass
1. es zwischen Knoten $u,v \in C$ einen Pfad $u$ nach $v$ gibt
2. es keine Menge $D\subseteq V$ mit $C\subset D$ gibt, die für die 1. auch gilt ($C$ ist maximal)
Ein Graph kann mehrere starke Zusammenhangskomponenten (strongly connected components, SCCs) haben

### Eigenschaften
![[Pasted image 20240728144028.png|]]

### SCC Algorithmus

**Ansatz**: 
- Lasse zweimal DFS laufen:
- Auf $G$ und auf transponiertem Graphen $G^T:=(V,E^T)$ mit $E^T:=\{ (v,u):(u,v) \in E\}$ (Kanten umgedreht)
![[Pasted image 20240728144740.png]]
=> SCCs bleiben im transponierten Graphen gleich, nur Übergänge drehen sich um
### Algortihmus

`SCC(G) //G=(V,E) directed graph`
```java
run DFS(G)
compute G^T
run DFS(G^T) but visit vertices in main loop in descending finish time from 1
output each DFS tree in 3 as one SCC
```

#### Beispiel:
![[Pasted image 20240728145322.png]]
1. zuerst DFS beim ersten Graphen
2. dann traversieren
3. Den Stack behalten wir evtl voll
4. von Stack runter arbeiten und nochmal DFS um zu sehen wie viele und wo SCC ist
### Algorithmendesign
![[Pasted image 20240728150053.png]]


## Minimale Spannbäume
Für einen zusammenhängenden, ungerichteten, gewichteten Graphen $G=(V,E)$ mit Gewichten $w$ ist der Subgraph $T=(V,E_{T})$ von $G$ ein **Spannbaum** ("spanning tree"), wenn T azyklisch ist und alle Knoten verbindet.
Der Spannbaum ist **minimal**, wenn 
$$w(T)=\sum_{\{ u,v \}\in E_{T}} w(\{ u,v \})$$
minimal für alle Spannbäume von $G$ ist.

--> Man nimmt der Reihe nach immer größere Kanten, aber man fängt bei der kleinsten an, sobald dies zum Zyklus führt, wird nächstgrößere Kante genommen
![[Pasted image 20240728150911.png]]
 $\text{Anwendung: Broadcast in Netzwerken}$

## Allgemeiner MST-Algorithmus
`genericMST(G,w) //G=(V,E) undirected, connectet graph, w weight function`
```java
A=Ø
WHILE A does not form a spanning tree for G DO
	find safe edge {u,v} for A
	A=A U {{u,v}}
return A
```
- `A` Teilmenge der Kanten eines MST
- Kante `{u,v}` ist sicher wenn $A\cup \{ \{ u,v \} \}$ noch Teilmenge eines MST ist

![[Pasted image 20240728155243.png]]
## Algorithmus von Kruskal
Kruskal lässt parallel mehrere Unterbäume eines MST wachsen.
Funktioniert auch für negative Kantengewichte
`MST-Kruskal(G,w) //G=(V,E) undirected, connected graph, w weight function`
```java
A=Ø
FOREACH v in V DO set(v)={v};
sort edges according to weight in nondecreashing order
FOREACH {u,v} in E according to order DO
	IF set(u)!=set(v) THEN //u and v connected otherwise
		A=A U {{u,v}}
		UNION(G,u,v);
return A
```
- Jeder Knoten hat Attribut `set`
- `UNION(G,u,v)` setzt $set(w)=set(u)\cup set(v)$ für alle Knoten $w\in set(u)\cup set(v)$
- $set(u),set(v)$ sind disjunkt oder identisch
![[Pasted image 20240728160749.png]]

Laufzeit: mit vielen Optimierungen (komplexere Datenstruktur,...): 
Laufzeit $=O(|E|\cdot\log|E|)$
Laufzeit normal $=O(|E|\cdot\log|V|)$
## Algorithmus von Prim
konstruiert MST Knoten für Knoten
Funktioniert auch für negative Kantengewichte

`MST-Prim(G,w,r) // r root in V, MST given through v.pred values`
```java
FOREACH v in V do {v.key=∞;v.pred=NIL;}
r.key=-∞; Q=V;
WHILE !isEmpty(Q) DO
	u=EXTRACT-MIN(Q); //smalles key value
	FOREACH v in adj(u) DO
		IF v€Q and w({u,v})<v.key THEN
			v.key=w({u,v});
			v.pred=u;
```
- **Idee**: Fügt, beginnend mit dem Wurzelknoten, immer leichte Kante zu zusammenhängender Menge hinzu
- Auswahl der nächsten Kante gemäß `key`-Wert, der stets aktualisiert wird
- A impliziert definiert durch $A=\{ \{ v,v.pred \} : v\in (V\setminus \{ (r \}\cup Q))\}$
![[Pasted image 20240728161616.png]]
![[Pasted image 20240728161626.png]]
**Erklärung:**
1. Wir fangen bei r an
2. es wird immer der kürzesten Kante gefolgt
3. solange bis 1 vor Zyklus
Laufzeit $=O(|E|+ |V|\cdot \log|V|)$

## Kürzeste Wege in (gerichteten Graphen)

## Single-Source Shortest Path(SSP)
Finde von Quelle s aus jeweils den kürzesten Pfad zu allen anderen Knoten
Kürzester Pfad: Gesamtgewicht reduzieren, Länge egal
Länge eines Pfades $p :=(v_{1},\dots,v_{k})\in V^k$ von $u=v_{1}$ zu $v=v_{k}$
- $w(p):=\sum^{k-1}_{i=1} w((v_{i},v_{i+1}))$
- $$shortest(u,v):=\begin{cases} \min\{ w(p):\text{p Pfad von u nach v} \} & \text{  wenn v erreichbar von u} \\
\infty   &sonst \\

\end{cases}$$
## SSSP vs BFS, DFS, MST
- BFS, DFS beachten Kantengewichte nicht
- BFS findet kürzeste "Kantenwege" nicht kürzeste Gewichtswege
- MST (für ungerichtete Graphen) minimiert Gesamtgewicht des Baumes
	- Dies bedeutet nicht unbedingt eine Minimierung der Gewichtswege
![[Pasted image 20240728164240.png]]

**MST**
![[Pasted image 20240728164312.png]]

## Zyklen und negative Kantengewichte
- Negative Kantengewichte sind erlaubt
- Zyklen mit negativem Gesamtgewicht sind nicht erlaubt
- Kürzeste Pfade können keine Zyklen mit positivem Gesamtgewicht haben
- Kürzeste Pfade enthalten höchstens Zyklen mit Gesamtgewicht 0
- Es gibt stets einen kürzesten Pfad mit Kantenlänge $\leq|V|-1$
## Kürzeste Teilpfade
- Teilpfad $s\to x$ eines kürzesten Pfades $s\to x\to z$ ist auch kürzester Pfad von $s$ nach $x$
- Sonst gäbe es ja kürzeren Pfad von $s$ nach $x$

## Algorithmen für SSSP
- Gemeinsame Idee: Lockerung/Relaxation
- [[#Bellmann-Ford]] funktioniert allgemein, auch ungerichtet
	- Laufzeit $=\theta(|V|\cdot|E|)$
- Algorithmus für Dags(Gerichtete, azyklische Graphen) funktioniert nur für dags
	- Laufzeit $=O(|V|+|E|)$
- [[#Djikstra]] funktioniert nur für nicht-negative Kantengewichte, auch ungerichtet
	- Laufzeit $= O(|V|\cdot \log|V|+|E|)$


## relax, initSSSP

`relax(G,u,v,w)`
```java
IF v.dist > u.dist + w((u,v)) THEN
	v.dist=u.dist+w((u,v));
	v.pred=u;
```
Verringere aktuelle Distanz von Knoten $v$, wenn durch Kante $(u,v)$ kürzere Distanz erreichbar
`ìnitSSSP(G,s,w)`
```java
FOREACH v in V DO
	v.dist=infinity;
	v.pred=NIL
s.dist=0;
```
Zu Beginn: Distanz $=\infty$ für alle Knoten $\neq s$


## Bellman-Ford
`Bellman-Ford-SSSP(G,s,w)`
```java
initSSSP(G,s,w);
FOR i=1 TO |V|-1 DO
	FOREACH (u,v) in E DO
		relax(G,u,v,w);
FOREACH (u,v) in E DO
	IF v.dist>u.dist+w((u,v)) THEN
		return false;
return true;
```

![[Pasted image 20240728175650.png]]
- **Erklärung**: Geht jede Iteration die alphabetische Ordnung einmal durch und schaut auf die Pfeile, die von den Wurzeln weg verweisen
- Tabe bekommt nur ein Update, wenn der weg verkürzt wird
- Falls keine änderung, wird true zurückgegeben

## SSSP mittels topologischer Sortierung

`TopoSort-SSSP(G,s,w) // G dag`
```java
initSSSP(G,s,w);
execute topological sorting
FOREACH u in V in topological order DO
	FOREACH v in adj(u) DO
		relax(G,u,v,w);
```
![[Pasted image 20240728180229.png]]

**Erklärung**:
1. $s=1$ in $1$, deswegen fangen wir bei 1 an und rotieren von dort aus alle Entfernungen
2. nachdem wir mit den Pfeilen von 1 durch sind, schauen wir uns die 2 an und falls es von dort verkürzte Entfernungen gibt, aktualisieren wir diese
3. Nach der Reihe gehen wir alle Zahlen durch, bis wir dann am Ende die kürzesten Wege gespeichert haben
Laufzeit $\theta(|E|+|V|)$

## Djiksta-Algorithmus
`Djikstra-SSSP(G,s,w)`
```java
initSSSP(G,s,w);
Q=V; // S=V-Q
WHILE !isEmpty(Q) DO
	u=EXTRACT-MIN(Q);
	FOREACH v in adj(u) DO
		relax(G,u,v,w);
```
Voraussetzung: $w((u,v))\geq 0$ für alle Kanten

![[Pasted image 20240728181520.png]]
![[Pasted image 20240728181533.png]]
**Erklärung**
- Wir fangen bei der ersten Node an und checken alle Nachbarn ab, doch nehmen wir immer den kürzesten Weg von jeder Node zuerst
- Wenn wir dann einen kürzeren Weg zu einen Node gefunden haben, aktualisieren wir den Wer und den Vorgänger
Laufzeit $\theta (|V|\cdot \log|V| +|E|)$ mittels Fibonacci-Heaps
## A*-Algorithmus
- Suche kürzesten Weg von $s$ zu einem Ziel $t$
- Dijkstra sucht lokal vom gegenwärtigen Punkt aus günstigsten nächsten Schritt, ignoriert aber Zielrichtung
- Füge Heuristik hinzu, die vom Ziel her denkt

`A*(G,s,t,w)`
```java
init(G,s,t,w);
Q=V;//let S=V-Q
WHILE !isEmpty(Q) DO
	u=EXTRACT-MIN(Q); //minimum über u.dist + u.heur
	IF u==t THEN break;
	FOREACH v in adj(u) DO
		relaX(G,u,v,w);
```
Jeder Knoten $u$ bekommt noch zuätzlichen Wert `u.heur` zugewiesen (Beispiel: Abstand Luftlinie vom Ziel)

A* findet optimale Lösung, wenn gilt:
1. Heuristik überschätzt nie tatsächliche Kosten
		`u.heur` $\leq shortest(u,t)$
2.Heuristik ist monoton, d.h für alle $(u,v)\in E$ gilt:
		`u.heur` $\leq w(u,v) +v.heur$

- Dijkstra ist mit A* mit Heuristik 0
- A* mit monotoner Heuristik ist Dijkstra mit Kantengewichten `w(u,v)+v.heur-u.heur` und `s.dist==s.heur`
	- A und Dijkstra wählen dann gleiche, Knoten, da `u.dist+u.heur==u.dist,t.dist==d.dist`
![[Pasted image 20240728183914.png]]

## Maximaler Fluss in Graphen

## Netzwerkflüsse

#### Idee
Kanten haben (aktuellen) Flusswert und (maximale) Kapazität
Ziel: Finde maximalen Fluss von $s$ nach $t$
Jeder Knoten außer $s$ und $t$ hat gleichen ein-und ausgehenden Fluss

Ein **Flussnetzwerk** ist ein gewichteter, gerichteter Graph $G=(V,E)$ mit Kapazität(sgewicht) $c$, so dass $c(u,v)\geq 0$ für $(u,v)\in E$ und $c(u,v)=0$  für $(u,v)\notin E$ mit zwei Knoten $s,t\in V$ (Quelle und Senke), so dass jeder Knoten von $s$ aus erreichbar ist $t$ von jedem Knoten aus ereichbar ist

Ein **Fluss** $f:V\times V \to \mathbb{R}$ für ein Flussnetzwerk $G=(V,E)$ mit Kapazität $c$ und Quelle $s$ und Senke $t$ erfüllt:
- $0\leq f(u,v)\leq c(u,v)$ für alle $u,v \in V$ (Fluss zwischen 0 und max. Kapazität)
- sowie für alle $u\in V-\{ s,t \}$: $\sum_{v\in V} f(u,v)=\sum_{v\in V} f(v,u)$
## Maximale Flüsse
Der Wert $|f|$ eines Flusses $f: V\times V \to \mathbb{R}$ für ein Flussnetzwerk $G$ mit Kapazität $c$,
Quelle $s$ , Senke $t$ ist $\vert{f}\vert:=\sum_{v\in V}f(s,v)-\sum_{v\in V}f(v,s)$

## Transformationen
![[Pasted image 20240728190259.png]]

## Ford-Fulkerson-Methode
Suche Pfad von $s$ nach $t$, der noch erweiterbar (bzgl. des Flusses) ist, Pfad wird im Restkapazitätsgraphen gesucht, der die möglichen Zu- und Abflüsse beschreibt

### Reste
Restkapazität $$c_{f}(u,v):=\begin{cases}
c(u,v)-f(u,v) && falls (u,v)\in E \\ \\
f(v,u) && falls (u,v) \in E \\
0 && sonst
\end{cases}$$
Fall 1: Wie viel eingehenden Fluss über $(u,v)$ könnte man zu $v$ hinzufügen
Fall 2: Wie viel abgehenden Fluss über $(u,v)$ kann man wegnehmneun und so zu $v$ hinzufügen?
Wohldefiniert, da nach Transformation nicht mehr sowohl $(u,v)$ als auch $(v,u)$ im Netzwerk sind

## Restkapazitäts-Graph
$G_{f}:=(V,E_{f})$ mit $E_{f}:=\{(u,v)\in v\times V:c_{f}(u,v) >0   \}$
Im Restkapazitäts-Graphen sind antiparallele Kanten erlaubt
![[Pasted image 20240730184957.png]]
## Restkapazitätem ausnutzen
Finde Pfad $s$ zu $t$ in $G_{t}$ und erhöhe (für Kanten in $G$) bzw erniedrige (für Gegenrichtung) um Minimum $c_{f}(u,v)$ aller Werte auf dem Pfad in $G$

## Ford-Fulkerson-Algorithmus
`Ford-Fulkerson(G,s,t,c)`
```JAVA
FOREACH e in E DO e.flow=0;
WHILE there is path p from s to t in G_flow DO
	c_flow(p)=min{c_flow(u,v):(u,v) in p}
	FOREACH e in p DO
		IF e in E THEN
			e.flow=e.flow+c_flow(p)
		ELSE
			e.flow =e.flow-c_flow(p)
```
$G_{f}$ ist `G_flow`, $c_{f}$ ist `c_flow`
### Beispiel
![[Pasted image 20240730185640.png]]
**Erklärung**
- wir nehmen Weg von $s$ nach $t$ und nehmen das Maximum von der kleinsten Kante und addieren des überall dann
- Wenn Kante voll ist, dann Richtungswechsel
- Wir laufen so viele Wege von $s$ nach $t$, bis es nicht mehr geht
- Alle $c_{flow}$ werden zsmaddiert und das ist dann de Kapazität
### Korrektheit des Ford-Fulkerson-Algorithmus

Sei $f:V\times V\to \mathbb{R}$ Fluss für ein Flussnetzwerk $G=(V,E)$ mit Kapazität $c$
und Quelle $s$ und Senke $t$. Dann sind äquivalent:
1. $f$ ist ein maximaler Fluss von G
2. Der Restkapazitätsgraph $G_{f}$ enthält keinen erweiterbaren Pfad
3. $|f|=min.c(S,V-S)$ mit $s\in S$ und $t\in V-1$

wobei: $c(S,V-S)=\sum_{u\in S} \sum_{v\in V-S} c(u,v)$

---
# Advanced Designs
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

