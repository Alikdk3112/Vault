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

