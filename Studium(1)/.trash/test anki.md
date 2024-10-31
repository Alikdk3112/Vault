### Collection

-> Sammlungen von Elementen (Elemente sind Objekte eines bestimmten Typs)

-> dieser Typ ist als generischer Typparameter offengehalten

- in Collection gibt es keine Reihenfolge der Elemente

- List, Map und Set

![[Pasted image 20240329235321.png]]

Bsp.

```java

Collection<Number> c1 = new ArrayList<Number> ();

```

-> Typparameter muss identisch sein (Number -> Number)

  

> Konstruktor mit leerer Parameterliste richtet jeweils eine leere Sammlung von Elementen ein

  

```java

for ( int = 0; i < 100; i++ ) {

    c1.add(new Integer(i));

}

```

> Objekt wird mir 100 Elementen gefüllt

  

`.add();` -> zum Einfügen eines neuen Elements

  

`.addAll();` -> erhält eine andere Collection als Parameter und fügt alle

              Elemente aus dieser Collection in das Collection-Objekt ein, mit dem die Methode aufgerufen wird

`.size();`-> hat keine Parameter und gibt als `int` die Anzahl der Elemente aus

  

`.isEmpty();` -> parameterklos, boolesch, liefert `true`wenn Collection keine

              Elemente enthält

  

`.contains();` -> boolesch, Parameter vom Typ Object

-> ein Objekt kann mit contains darauf getestet werden, ob es in der Collection

    mindestens einmal enthalten ist

```java

Collection<String> coll = new....;

String str1 = new String ("Hallo");

String str2 = new String ("Hallo");

coll.add(str1);

if(coll.contains(str2))

```

  

`.containsAll();` -> ganze Collection als formalen Parameter, liefert `true`,

                   wenn contains für alle Elemente in dieser Collection `true`zurückliefert

  

`.clear();` -> parameterlos, entfernt sämtliche momentan gespeicherte

            Elemente aus der Collection, mit der diese Methode aufgerufen wird

  

`.remove()` -> boolesch, Parameter vom Typ Object, liefert true im selben Fall

            wie contains zurück

            -> eines dieser Vorkommen des Parameters wird aus der

                Collection entfernt

  

### List

-> das Interface List erweitert das Interface Collection

- in einer Liste ist auf den Elementen eine Reihenfolge definiert

- Elemente können wie bei Array über einen Index angesprochen werden

  

`.indexOf();` -> Parameter vom Typ Object, liefert ersten Index zurück, an

               dem der Parameter zu finden ist

               - falls der Parameter nicht in der Liste gefunden wird, so wird der "unmögliche Index" -1 zurückgeliefert

`.set();` -> zwei Parameter (Index, Parameter vom Elementtyp)

            - der Wer, der in der Liste momentan an diesem Index gespeichert wird, wird durch den zweiten Parameter ersetzt

```java

T set ( int index, T element) throws ...

```

  

- Rückgabe ist der alte Wert, also das Element, das vorher an dem Index war

- überschreibt das Element am gegebenen Index mit einem neuen Wert

  

`.add();` -> hat wie .set neben dem einzufügendem Element noch einen Index als

            Parameter

- fügt das neue Element an diesem Index ein, ohne ein anderes Element zu entfernen

- neues Element wird vor dem Element eingefügt, das bisher am angegebenen Index stand

- alle Elemente mit höherem Index rutschen entsprechend um 1 in ihrem Index weiter

  

`.get();` -> ganzzahligen Index als Parameter, liefert das Element an dieser

            Position zurück

  

### Wildcards auf Collections und Listen

  

```java

public boolean containsNull (Collection<? extends Number> coll) {

    return coll.contains(null);

}

```

  

```java

public double getValue (List<? extends Number> list, int index) {

    return list.get(index).doubleValue();

}

```

  

### Listen von Lambda-Ausdrücken

Bsp.

```java

List<IntPredicate> predicates = new....();

predicates.add ( n -> n % 2 == 1);

predicates.add (n -> n > 0);

predicates.add ( n -> n * n < 100);

predicates.add ( predicates.get(0).negate());

predicates.add ( predicates.get(1).and( predicates.get(2)));

predicates.add ( predicates.get(3).or( predicates.get(4)));

```

- bei Listen muss die add-Methode aufgerufen werden

- `.get();`wird benötigt, um auf ein Listenelement zuzugreifen

  

### Sortieren mit Comparator

Bsp.

```java

List<Student> list = new LinkedList<Student> ();

  

for ( int i = 0; i > 100000; i++) {

    Student s = new Student();

    s.enrollmentNumber = ((5432 * i) % 4321);

    list.add(s);

}

  

Collections.sort( list, new EnrollmentNumberComparator());

```

> Liste mir der Klasse Student wird eingerichtet

> Matrikelnummern werden zugewiesen

> Student-Objekte werden mit diesen Matrikelnummern in die Liste eingefügt

  

###### Klassenmethode `.sort();`,

- sortiert die Liste, also den ersten Parameter der Methode

- Sortierlogik wird durch den zweiten Parameter definiert, der eine Comparator-Klasse mit demselben Typparameter wie die Liste sein muss

  

### Iterator

-> generisches Interface

-> bietet Möglichkeit, Schritt für Schritt durch Sammlungen zu laufen

```java

Iterator<Number> it1 = c1.iterator();

Iterator<Number> it2 = c2.iterator();

Iterator<Number> it3 = c3.iterator();

  

while ( it.hasNext()) {

    System.out.print ( it.next().doubleValue());

}

```

  

`.iterator();` -> liefert ein Objekt ihrer eigenen spezifischen Iterator-Klasse

                zurück

`.next();` -> liefert das nächste Element in der Aufzählung und setzt die Position

            weiter

`.hasNext();` -> liefert `true`, falls die Iteration weitere Elemente bietet

  

#### Kurzform for-Schleife

```java

public void writeAllElements ( Collection<String> coll) {

    for (String str : coll) {

        System.out.print( str);

    }

}

```

> Variable vom Elementtyp der Collection enthält nacheinander Verweise auf die einzelnen String-Objekte, die in er Collection momentan gespeichert sind

> - nach Doppelpunkt -> Name der Collection

  

#### Standardoperationen filter, map und fold

**Standardoperation filter**

```java

Objektmethode von Collection <T>:

    boolean removeIf ( Predicate<? super T> pred)

```

- alle Elemente, die das Prädikat passieren, werden aus der Collection entfernt

- zurückgeliefert von removeIf wird, ob mindestes ein Element aus der Collection entfernt wurde, oder nicht

  

> entspricht nicht der filter-Operation in Racket, denn dort word eine neue Liste zurückgeliefert, nicht die Eingabeliste geändert

  

`.remove();` -> entfernt das letzte mit .next() zurückgelieferte Element

  

#### Bsp. wie bei Racket

-> separate Ergebnisliste wird erstellt

```java

public static <T> Collection <T> filter (Collection <T> coll, Predicate <T> pred) {

  

    Collection<T> result = new LinkedList<T> ();

    for ( T t : coll) {

        if( pred.test (t)) {

            result.add (t);

        }

    }

    return result;

}

```

  

 **Standardoperation map**

 ```java

public static <X,Y> Collection <Y> map (Collection <X> coll, Function<X,Y> fct) {

  

    LinkedList<Y> result = new LinkedList<Y>();

    for ( X x : coll) {

        result.add ( fct.apply(x));

    }

    return result;

}

 ```

**Standardoperation fold**

```java

public static <X,Y> Y fold ( Y init, BiFunction<X,Y,Y> fct, Collection <X> coll ) {

  

    y tmp = init;

    for( X x : coll) {

        tmp = fct.apply(x, tmp);

    }

    return tmp;

}

```

  

### Maps

- Abbildungen, Funktionen im Sinne der Mathematik

  

```java

Map<String, X> map = new HashMap <String, X> ();

  

for (inr i = 0; i < 100; i++) {

    String key = "Nr." + i;

    X value = new X (2 * i + 3);

    map.put(key, value);

}

```

- Interface Map hat zwei Typparameter

    -> der erste ist `key`

    -> der zweite ist die Information, die zum `key` gespeichert wird (`Value`)

- Map realisiert eine Abbildung von `keys`in die `Values`

  

> die `keys` in einer Map müssen alle unterschiedlich sein

  

`.put();` -> Paar wird eingefügt

  

### Eigene LinkedList-Klasse

```java

public class ListItem<T> {

    public T key;

    public ListItem<T> next;

}

```

> Klasse ListItem ist zweckmäßigerweise generisch

> - Listenelement wird als `Key`bezeichnet

  
  

![Linked Lists](https://www.cs.usfca.edu/~srollins/courses/cs112-f07/web/notes/linkedlists/ll2.gif)

  

```java

public class MyLinkedList<T> implements List <T> {

    private ListItem<T> head;

    ...

}

```

-> Verweis auf den Kopf der Liste

  

```java

ListItem<T> p = head;

```

> Laufpointer `p` soll nacheinander auf die einzelnen Elemente der Liste verweisen

```java

p = p.next;

```

-> Abbruchbedingung: p == null

```java

public void processAll ( Consumer <T> consumer ) {

    for (ListItem<T> p = head; p!= null; p = p.next) {

        consumer.accept( p.key) ;

    }

}

```

> for-Schleife zum Durchlauf durch die Liste

> Pointer p wird initialisiert

  

#### neues Element einfügen:

->  am Anfang der Liste

```java

ListItem<T> tmp = new ListItem<T>(); //neues Listenelement

tmp.key = key;

tmp.next = head

head = tmp;

```

> z1. neues Listenelement wird erstellt

> z2. Listenelement bekommt den einzufügenden Schlüssel als Attribut key

> z3. neues Element muss auf den bisherigen Listenkopf verweisen

> z4. head wird auf den neuen Listenkopf gesetzt

  
  

-> mitten in der Liste:

```java

ListItem<T> tmp = new ListItem<T> ();

tmp.key = key;

```

- müssen wieder Laufpointer p einrichten

- wenn das neue Element die Position n bekommen soll, dann muss p auf der Position n - 1 stehen

```java

tmp.next = p.next;

```

> analog zum Einfügen am Listenanfang

> - zuerst wird das next-Attribut des neuen Listenelements auf die Adresse desjenigen Objekts gesetzt, das dem neuen Listenelement nach dem Einfügen unmittelbar folgen soll

  

```java

p.next = tmp;

```

> Verweis, der auf das neue Listenelement zeigen soll, wird gesetzt

  

komplett:

```java

ListItem<T> tmp = new ListItem<T> ();

tmp.key = key;

p.next = tmp;

tmp.next = p.next;

p.next = tmp;

```

  

Fall, dass das neue Listenelement ganz vorne, also an Position 0 einzufügen ist:

```java

if ( pos == 0) {

    if ( head == null) {

        head = tmp; /*neues Element wird als Kopf gesetzt, wenn

                      kein Element drin ist*/

    }

    else {

    tmp.next = head;

    head = tmp;

    }

    return;

  

}

```

  

#### Element entfernen:

```java

head = head.next;

```

> beim Entfernen eines Elements müssen wir zwischen Listenkopf und Listenelementen unterscheiden

> -  beim Entfernen des Listenkopfes -> Listenkopf wird sozusagen übersprungen

  

```java

p.next = p.next.next;

```

> Überspringen auch im Fall, dass ein Element irgendwo mitten in der Liste entfernt werden soll

> - Inhalt des next-Attributs muss verändert werden

  

```java

public boolean remove (Object obj) {

    if (head == null) {

        return false;

    }

    if ( Objects.equals(obj, head.key)) {

        head = head.next;

        return true;

    }

  

}

```

> Methode `.equals();` zum Suchen des zu entfernenden Elements

> head = head.next zum Überspringen des ersten Listenelements

  

```java

for ( ListItem<T> p = head; p.next != null; p = p.next) {

    if( Objects.equals(obj, next.key)) {

        p.next = p.next.next;

        return true;

    }

    return false;

}

```

> wird vorausgesetzt, dass auch p.next existiert

  

**Iteratorklasse**

```java

class MyLinkedListIteratpr<T> implements Iterator <T> {

    private ListItem<T> p;

  

    public MyLinkedListIterator (ListItem<T> head) {

        p = head;

    }

    ....

}

```

> Iterator als ein Verweis auf ein Listenelement, als Attribut

> - dieses Attribut wird im Konstruktor des Iterators auf den Kopf der Liste gesetzt

> - `p`wird mit `hasNext`auf das nächste zurückliefernde Element verwiesen, also auf das erste in der Liste, dessen `key`noch nicht durch `hasNext`zurückgeliefert wurde

  

```java

public iterator<T> iterator() {

    return new MyLinkedListIterator ( head);

}

```

  

### Doppelt verkettete Listen

-> vorwärts und rückwärts verkettet

- Vorteil: man kann Liste in beiden Richtungen gleichermaßen durchlaufen

- Nachteil: mehr Speicher wird benötigt, Einfügen und Entfernen kostet mehr

          Laufzeit

  ![[Pasted image 20240330151217.png]]

  > zwei Verweise auf andere Elemente in jedem Listenelement

### zyklische Listen

- letzter Verweis nicht auf null, sondern wieder auf das erste Element

- keine lineare Liste mehr -> zyklische Liste
