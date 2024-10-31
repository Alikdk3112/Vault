## Aufgabe 2 a)

```java 
public interface <X,Y extends Button>Inf1{

public boolean itIsSo(Y y);

default public void add(Window window, X x){

if(x instanceof Button){

window.add(x);    //**Fehler**! casting von x muss sein -> windwo.add((Component) x)

}

else { 
window.add(new Button("Hello"));
}

}

}
```

- Immer public zur sicherheit schreiben
- Wenn eine Typ auf einen anderen Typ und seinen Typ beschränkt ist -> `extends`
- instanceof kleinschreiben
-  Falle in dem Fall, weil Typ X nicht von Component erbt und in den Paramter ein Component erwünscht ist.
- In der Aufgabe Methodenimplementation zweitrangig, Kopf schreiben ist wichtiger 
## Aufgabe 2 b)

```java
public //abstract fehlt hier, da das Interface implementiert wurde aber die Methode dazu nicht!!!
class <X, Y extends Buttom>Class1 // Class1<X,Y extends Buttom> 
implements Inf1<X, Y extends Buttom>, Function<X, Y extends Buttom>{       // implements Inf1<X,X>, Function<Y,X>

public Y apply (X x){

return null;

}

}

```
- Vererbung von generischen Klasse-> `Y extends Buttom` reicht im Klassenkopf, wird mitvererbt.
- Generische typparamter-> deklaration und benutzung der Typparameter. Y extends Button wäre falsch bei den Interfaces, da Y schon "deklariert" wurde -> Ähnlich wie Variablen
- Generische Typparameter nach dem Klassennamen
- default Methoden  müssen nicht nochmal implementiert werden

## Aufgabe 2 c)

```java
public Class2 <X,Y extends Bottom>  
extends Class1<X,Y extends Bottom>{   // !!!Fehler Class <X,Y> siehe aufgabe 2b

public boolean itIsSo(Y y){

return true;

}

}
```
- direktes erben -> extends der Klasse
- indirektes erben -> extends einer Klasse die selber extends wurde

## Aufgabe 3a)
```java
public class Exc1 extends Exception{

public Exc1(List<Number> list,){
super (
(list == null)? "" : (list.isEmpty()?) "empty" : list.get(0).toString()

);
}
}
```
- [[ternärer Operator]] angucken

## Aufgabe 3b)
```java
public static double m(double a, double b) throws Exc1 {

LinkedList<Number> list = new LinkedList<>();

list.add(a);

list.add(b);

if(a<0 && b<0){

throw new Exc1(list);

}

if(a <0 || b < 0){

throw new ArithmeticException();

}

return a; //optional mit else

}
```
 
- `static` methode darf nie `abstract` sein
- *optional* `LinkedList<Number> lst = new Linked<Number>();` ->Number in beide <> schreiben
- Deklarieren von `throws` von **RuntimeExceptions** ist optional.-> bei Unsicherheiten lieber mit schreiben
## Aufgabe 3c)

```java
public Thread m2 (int c, int d, Runnable runny)throws Exc2,Exc1{

try{

m(c,d);
//return new Thread(runny)

}

catch( Exc1 e){

// weitergreicht ? -> throw e //optional

}

catch(ArithmeticException e){

throw new Exc2;

}

return new Thread(runny); // return Typ kann man auch in try einschließen

}
```

- Weitergereicht -> `throw e` -> ist jedoch optional
- double umfasst mehr zahlen als int, daher ist hier nicht casten okay
- da Exc2 keine RuntimeException ist, -> muss oben bei throws
- return muss in try oder hinter dem catch geschrieben werden, hauptsache nicht im Catchblock.


# Aufgabe 4d) (rekursiv)
```java
public <T> void foo(List<T> lst1, List<T>lst2, ListItem<T> tail){

if(lst == null){

return null;

}

if(bar(lst1.key,lst2)) // weil bar boolean ist
{

}

public <T> boolean bar(T key, ListItem<T> lst){

if(lst == null){

return false;

}

else if (key.equals(lst.key)){

return true;

{

else {

// !!! return hinschreiben
bar(key, lst.next);

}

}

}

}
```
- ##### Foo:
	- 2. if Anweisung :
```java
	ListItem<T> tmp = new ListItem<>();
	tmp.key = lst.key //key von lst 1 auf tmp setzen

	tail.next = tmp; //momentanes Element verweisen wir auf unser neues
	tail = tmp;      //tail abändern
```

# Aufgabe 4b)


# Aufgabe 4c)



# Aufgabe 5)

```java


`