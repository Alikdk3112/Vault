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

