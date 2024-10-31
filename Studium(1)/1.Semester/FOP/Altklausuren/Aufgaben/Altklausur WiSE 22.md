
# Aufgabe 1 a) 
```java
public interface X<A extends Canvas & IntPredicate>{

default public <B extends Component> boolean def(LinkedList<? super Integer> x, B y){

if (x == null){

return false;
}
  if(y instanceof Canvas){
  x.add(1);
  }
  else{
  x.add(-1);
  }

}

public Double fct (BiFunction<A,Integer,Double> op,  A a);

 }

```

# Aufgabe 1b) 

```java
public abstract class Y<A extends Canvas & IntPredicate> implements X<A>, Consumer<A>{

public Double fct( BiFunction<A,Integer, Double> op, A a){

op.apply(a,+2);

 }
```





# Aufgabe 2a)

```java 

public class Exc3 extends Exc1{

public Exc3(Supplier<String> supp){

super(

(supp==null || sup.get() == null)? 0 : 1

)

  }

  }

```


# Aufgabe 3 
```java

public ListItem<T> foo(ListItem<T> lst1,ListItem<T> lst2){

if (lst1 == null){

return bar(lst2, null);

 }

}

else{ 

ListItem<T> tmp = new ListItem<>();

tmp.key =lst1.key;

tmp.next = foo(lst1.next, lst2);

return tmp;

}

```

## !! cons 
```java
- ListItem<T> tmp = new ListItem<>();

tmp.key =lst1.key;

tmp.next = foo(lst1.next, lst2);
```
* rechte Seite->die parameter im racket code;






# Lambda Aufgaben (Aufgabe 4)
# a)
```java
public interface Foo{

public Integer apply(List<Integer> a, List<Integer> b);

   }

public class MyFoo implements Foo{

public Integer foo(List<Integer> a, List<Integer> b){

return a.get(0).intValue*b.get(0).intValue;

}

   }
```

# b)
```java
public interface Bar<T>{

public  boolean test(T c, T d, T e);

  }

public class MyBar implements Bar<Integer>{

public  boolean (Integer c, Integer d, Integer e){

  return (c<d) && (c<e);

  }

  }
```

# c)
```JAVA
public static BiFunction<List<Integer>,List<Integer>,Boolean> foobar(Bar<Integer> bar, Foo foo, Integer t1, Integer t2){

return  (x,y)-> bar.test(foo.apply(x,y),t1,t2 ));

   }

X.foobar();
```

-  Bei der letzten Aufgabe muss man den großen beispiel Aufruf implementieren-> foo und bar als lambda ausdrücke schreibenn reicht schon

# Array Aufgaben (Aufgabe 5)

# b) rekursiv:

```java 


```