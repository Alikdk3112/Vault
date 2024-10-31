# Interface Collection
- Sammlung von Elementen
- Elemente sind Objekte eines Bestimmten Typs.-> Dieser Typ ist generisch gehalten 

![[Pasted image 20240328151557.png|500]]
# ListItem 
- Generische Klasse
- Das eigentliche Element wird als Key bezeichnet
- die Elemente werden miteinander mithilfe des Attributes next verkettet.
```java 
public class ListItem <T>
public T key; // das Element
public ListItem<T> next; 
```



| ListItem                 | `ListItem<T> item = new ListItem<>()`;                 |
| ------------------------ | ------------------------------------------------------ |
| Wert eines Elements      | `item.key`                                             |
| Vergleichen des Elements | `item.key.equals(obj)`                                 |
| Anfangselement           | `item = head`                                          |
| Schlusselement           | `tail`                                                 |
| nächster wert            | `item.next`                                            |
| Abbruchbedingung         | `item = null`                                          |
| Durchlaufschleife        | `for(ListItem<T> p = head; item != null; p = p.next)'` |
|                          |                                                        |

---

# LinkedList
- `private ListItem<T> head;` -> Das erste Element der Liste
- Keinen Zugriff durch den einen Index wie bei "Arrays"
- Zum durchlaufen der Elemente verwendet man einen "pointer"
``` java
ListItem<T> pointer = head;

while (pointer != null){
pointer = pointer.next;
}
```

### Neues Element einfügen in LinkedLists

#### Fall Element wird vorne an Index 0 eingefügt

``` java
ListItem<T> tmp = new ListItem<T>(); // neues Listenelement, ein ListItem von T
tmp.key = key; // ListItem bekommt den einzufügenden Schlüssel als Attribut key
tmp.next = head; // das neue Element wird an den Kopf eingefügt

head = tmp;    // und dann wird head auf den Listenkopf gesetzt
```
/anki
##### Schritt für Schritt Anleitung
1. ListItem erstellen: `ListItem<T> tmp = new ListItem<>();` 
2. Key bestimmen : `tmp.key = key`
3. vor das erste Glied (head) hängen: `tmp.next = head`
4. als erstes Glied (head) benennen: `head = tmp`


- Reihenfolge muss so eingehalten werden
/dun
#### Fall Element wird irgendwo in der Mitte eingefügt
- 1. Erstellen: `ListItem<T> tmp = new ListItem<T>();`
- 2.Listendurchlauf bis zur Stelle wo es eingefügt werden soll
- 3.Key bestimmen `tmp.key = key;`
-  4.vor das nächste Glied (p.next) hängen : `tmp.next = p.next`
(p und tmp sind noch nicht verbunden, aber beide sind mit );
- 5.hinter das p Glied hängen `p.next = tmp;
- nun wurde das Glied zwischen rein geschoben, erst vorne, dann hinten.
### Beispielmethode zu add
- Instanzieren des Elements und Attribut key auf den einzufügenden Wert setzen
```java
public void add(int pos,T key){
ListItem<T> tmp = new ListItem<T>();
tmp.key = key;
}
```

- **Implementierung** :
```java
// wenn Liste leer ist
if (pos == 0){
if (head == null){
head = tmp;
}
else{
tmp.next = head;
head = tmp;
}
if (pos == 0){
tmp.next = head;
head = tmp;
return;
}
}
```
-  **Durchlaufen der Schleife**
```java 
for (listItem<T> p = head; p != null; p = p.next)//durchlaufen des pointers
{
pos--   //position wird verringert
if (pos == 0){ //wunschposition wird erreicht

tmp.next = p.next;
p.next = tmp          //anhängen des Elements in die Liste
return,
}
}
```
- Durchlauf wird dann abgebrochen, wenn pos den Wert 0 erreicht hat-> pointer hat die gewünschte Position erreicht
- Element wird dann eingesetzt
- `for (listItem<T> p = head; p != null; p = p.next)` äquivalent zu
- **`while (p!=null){p=p.next;}`**
---


## Iterator
- generisches Interface
- Schritt für Schritt durch die Collection

### Beispiel:

```java
Iterator<Number> it1 = c1.iterator();
Iterator<Number> it2 = c2.iterator();

while (it.hasNext()){
System.out.print(it.next().doubleValue)

}
```
- `.iterator();` liefert ein Objekt ihrer eigenen spezifischen Iterator-Klasse zurück
- `.next();` liefert das nächste Element in der Aufzählung und setzt die Position weiter
- `hasNext();`  liefert `true` wenn die Iteration weitere Elemente bietet