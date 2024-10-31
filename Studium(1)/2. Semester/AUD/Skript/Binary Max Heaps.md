## Definition:
- bis auf das unterste Level vollständig und im untersten Level von links gefpllt
- für alle knoten gilt : `x.parent.key >= x.key`
- *Keine BST,* links kann größer sein als rechts
- Bei Min-Heaps sind die Werte in Elternknoten  jeweils kleiner

# Eigenschaften:
-  Es gilt, $h \leq \log n$
- Maximum = Wurzel

# Heaps durch Arrays
-  Anzahl der Knoten werden in `H.length` gespeichert
- Duale Sichtweise als Pointer  oder als Array (j ist Index von Array)
	- j.parent = $\frac{j}{2} -1$
	- j.left = $2(j+1) -1$
	- j.right = $2(j + 1)$
![[Pasted image 20240617183514.png|400]]
# Einfügen 

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

# Lösche Maximum

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

# Heap-Sort

Gibt Einträge in Array A in absteigender größe aus
der Maximale Wert wird ausgegeben und gelöscht
`heapSort(H) // Array schon nach H.A kopiert`
```java
buildHeap(H); // Bauen des Heaps
WHILE !isEmpty do PRINT extraxt-max(H); // Ausgabe des Maximums bis Heap leer ist
```

# Abstrakter Datentyp Priority Queue
- ´`new(Q)` erzeugt neue, leere priority Queue namens q
- `isEmpty(Q)` gibt an, ob Queue Q leer ist
- `max(Q)` gibt größtes Element aus Queue Q zurück
- `extract-max(Q)` gibt größtes Element aus Queue zurück und löscht es aus Q
- `insert(Q,k)` fügt Wert k zu Queue hinzu, implementation kann priority Heap verwenden