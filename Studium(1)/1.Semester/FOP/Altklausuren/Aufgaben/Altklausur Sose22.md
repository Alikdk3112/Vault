# Aufgabe 1 a)


```Java
public interface Yep <X,Y extends Stream,Z extends Robot>{

public Z fm(Bifunction<X,Y,Z> fct, Y y);

public default <T extends Number> Z dm(List<? super String> x, Supplier<? extends String> y) {
String s = y.get();
while(s == null){

s=y.get();

}

x.add(0,y.get());
return null;
}

}


}
```



# Aufgabe 1 b)

```java
public abstract class Nope<X,Y extends Stream, Z extends Robot> implements Yep<X,Y,Z>, Consumer<Double>{

public Z fm(BiFunction<X,Y,Z>fct, Y y){

      return fct,apply(null,y);

}

}
```



# Aufgabe 1 c)

```java
public class YesOrNo<X, Y extends Stream , Z extends Robot> extends Nope<X,Y,Z>{

   public void accept(Double d){

    System.out.println(d);

}
```


# Aufgabe 2 a) 
```java

public class Exc3 extends Exc1{

public Exc3(Number n){

super(((n instanceof Byte)? n.intValue() : 2), // für den ersten Parameter
    
     ((n instanceof Byte)? 1 : 3)              // für den zweiten Parameter
         );

)

}

}

```

# Aufgabe 2 b)

```java
public static int m(Queue<Character> q, Button b)t throws !!!{

if (q == null){

    throw new Exc1 (5,6);

}

if (q != null && q.isEmpty()){   

throw new Exc2((byte) 7);

                       
        if(c != null && 'a' <= c && c <= 'z'){
               return 4;
         }

Number n = new Double(3.14)       

 throw new Exc3(Double.valueOf(3.14));

               }



}
```

# Aufgabe 2c)
```java

public Integer m(Queue<Character>q,int n) throws Exc3{

try{

     Y.m(q,new Button());

        }

catch( Exc2 e | Exc3 e){

   throw new Exc3(new Integer(5));

     }

  catch(Exc1){

     return n;

      }

return m;

}
```
- eingekapseltes Objekt -> `Integer.valueOf(xxx);`
- **Throws** Klausel nur die aufschreiben die auch geworfen werden
# Aufgabe 3a)

```java

public ListItem<T> foo(ListItem<T> lst){

if (lst == null){

return null;

  }

if (lst.next == null){
// kopie erstellen
listItem<T> tmp = new ListItem<T>();
tmp.key = lst.key
return tmp;

 }

ListItem<T>

  }

```
- `cond` -> `if, else if , else`

# Aufgabe 3b)

```java 
public void foo(ListItem<T> lst, ListItem<T> tail){

if (lst == null){

return null;

  }

else if (lst.next == null){
// kopie erstellen
listItem<T> tmp = new ListItem<T>();
tmp.key = lst.key
return tmp;


}
else{
ListItem<T> p = new ListItem<>();
p = lst;
while(p != null){

if(lst.next==0){

tail.next =
}


}

}

}

```

# Aufgabe 4a)#

```java
// foobar: Number,Number, Number, foo, bar
// bar:  Number,boolean, Number -> boolean
// foo : Number, Number-> Bool
```


```java
public interface Foo<T> {

public boolean test(T a, T b);


}

public class MyFoo<T> implements Foo<T>{

public boolean test (T a, T b){

return a == b;

}

}
```


# Aufgabe 4b )

```java

public interface Bar {

public boolean apply(long c, boolean d , long e);

}


public class MyBar implements Bar{

public boolean apply(long c , boolean d , long e){


return d && c<e;
}

}
```


# Aufgabe 4c)

```java

public static BiFunction<Long,Long,boolean> foobar(long t1, long t2, long t3,Foo foo, Bar bar){

return (x,y)-> {

bar.test(t1,foo.test((x*t2,y)),t3);

}

}

Y.foobar(3,4,5,(a,b)->a==b, (c, d, e)-> d&& c<e);
```

- **Y.foobar** am ende beispielaufruf:



# Aufgabe 5 a)

```java
public static int[] foo(int[] a){
int index = 0;
for (int i = 0; i<a.length ; i++){
if(a[2*i]>=a[2*i+1]){

index++;
}


}

int[] result = new Array[index];
int resultIndex = 0;
}

for (int i = 0; i<a.length;i++){

if(a[2*i]>=a[2*i+1]){

result[resultIndex] = a[2*i]
resultIndex++;
}

}

return result;


```

# Aufgabe 5b) (Rekursiv Array)


```java 
public static int[] foo(int[] a){


  }

public static int bar(int[] a, int index)


public static ??? foobar(int[]a,int index,int[] result, int resultIndex){


}
```
- 