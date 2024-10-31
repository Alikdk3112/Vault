``` java
public double m(X<? extends Number> n){}
```
- Mit Fragezeiche vor dem Typ Number wird festgelegt, dass n entweder von `Number` abgeleitet sein muss oder `Number`  ist.
- Wildcards ist die Methode **nicht** generisch
- nur einzelne Parameter sind generisch

```java 
public String m (X<?> x ){}
```
- einzelnes Fragezeichen-> Typ "`extends Object`" 
- => Durch `? extends`... wird also ein Hierarchielimit nach oben gesetzt
	- Werte dürfen **gelesen** werden, aber nicht überschrieben
- => Durch `? super...` kann man ein Limit nach unten setzen
	-  Werte dürfen **überschrieben** werden, aber nicht gelesen


## Erinnerung

- rekursiv <-> iterativ kann man idr einige parallelen ziehen
- rekursionsanker -> fortsetzungsbedingung schleife zb
- was im rekursiven aufruf verändert wird ist die fortsetzung bei erneutem schleifendurchlauf
- struktur ist immer dieselbe idr
- wenn syntax nicht passt dann liegt es evtl in der kulanz der person die bewertet
- wenn du kp hast methodenkopf gibt eig imemr 1p