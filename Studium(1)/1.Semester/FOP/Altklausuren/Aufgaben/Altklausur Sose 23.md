# Aufgabe 1 a)

```java
public interface X<O extends Object>{

   public boolean vrfy(BiPredicate<Double, O> pred, Double D, O o);

public default <T extends Number> void def(ArrayList<Number> alon, T t ){

     if(alon.size() >= 4 && t instanceof Integer){

          alon.set(3,t);

    }

else{     

      alon.add(0,4);

     }

 }

 }
```




















# Aufgabe 1b)
``` java
public abstract class Y<O extends Object> implements X<O>, ItemListener{

     public boolean vrfy(BiPredicate<Double, O> pred, Double d, O o){

            pred.test(d,o);

   }

  }
```

# Aufgabe 1c)
```java
public class Z<O extends Object> extends Y<O>{

   private int stateChange;

        public void itemStateChanged(ItemEvent e){

             stateChange = e.getStateChange;

    }

         }
```






















# Aufgabe 2a)
```java
public class Exc3 extends Exc2 {

public Exc3(List<Integer> lst){

    super( lst == null || lst.isEmpty? 0 : lst.get(0));

    }

  }
```

# Aufgabe 2b)
```java
public static int m(List<Integer> lst, Optional<Integer> i) throws Exc2{

if(lst == null){

    throw new Exc1();

   }

  if(i == null || i.isEmpty){

      throw new Exc2(1);

     }

     if (i.get().intValue < 0){

                  throw new Exc3(lst);

                   }

      return i.get().intValue();

 }
```



























# Aufgabe 2c)

```java
public int m2(List<Integer> lst) throws Exc3{

             try{

    return X.m(lst,Optional<Integer>.of(1));

               }  

          catch(Exc3 e ){

                     return -1;

                   } 

            catch(Exc1){

             throw new Exc3(lst);

              }

}
```































# Aufgabe 3a)

``` java
public  ListItem<Integer> foo(ListItem<Integer> lst1, ListItem<Integer> lst){

if (lst1 == null){

 return null;

  }

if(lst2 == null){

ListItem<Integer> tmp = new ListItem<Integer>();

tmp.key = lst1.key;

tmp.next = lst1.next;

return tmp;

  }

else{

ListItem<Integer> tmp = new ListItem<Integer>();

tmp.key = bar(lst1,lst2);

tmp.next = foo(lst.next, lst2);

return tmp;

  }

}

private int bar(ListItem<Integer> lst1, ListItem<Integer> ls2){

if (lst2 == null){

   ListItem<Integer> tmp = new ListItem<Integer>();

     tmp.key = lst1.key;

      return tmp.key;

    }

 if(lst1.key>=lst.key){

ListItem<Integer> tmp = new ListItem<>();

  tmp.key = lst2.key;

  return lst.key +bar(lst1, lst2.next);

    }

else{

return bar(lst1,lst2.next);

  }

}
```
























# Aufgabe 3b)
```java
public ListItem<Integer> foo(ListItem<Integer> lst1, ListItem<Integer> lst2){

ListItem<Integer> head = null;

ListItem<Integer> tail = null;

if(lst1 == null){

return null;

 }

if(lst2 == null){

 ListItem<Integer> tmp = new ListItem<>();

tmp.key = lst1.key;

tmp.next = lst1.next;

return tmp;

  }

ListItem<Integer> p = new ListItem<>();

p = lst1;

while (p != null){

if(head == null){

ListItem<Integer> tmp = new ListItem<>();

tmp.key = bar(lst1,lst2);

tmp.next = head;

head = tmp;

return head;

   }

ListItem<Integer> tmp = new ListItem<>();

tmp.key = bar(lst1,lst2);

tmp.next = tail;

tail= tmp;

return head;

p=p.next;   

}

 }

public int bar(ListItem<Integer> lst1, ListItem<Integer> lst2 ){

 ListItem<Integer> p = new ListItem<>();

 p = lst1;

while(p != null){

 if(p.key >= lst2.key){

     ListItem<Integer> tmp = new ListItem<>();

         tmp.key = lst2.key + p.key;

          return tmp.key;

         }

else{

ListItem<Integer> temp = new ListItem<Integer>();

temp.key = p.key;

   return tmp.key;

}

p = p.next;

     }

 }
```



















# Aufgabe 3c)
```java
public LinkedList<Integer> foo(List<Integer> lst1, List<Integer> lst2){

List<Integer> result = new LinkedList<Integer>();

Iterator<Integer> it1 = lst1.iterator();

Iterator<Integer> it2 = lst2.iterator();

while(it.hasNext){

result.add(bar(it1,it2));

   it = it.next;

   }

return result;

 }

public int bar(Iterator<Integer> lst1, Iterator<Integer> lst2){

int result = 0;

while(lst1.hasNext()){

if(lst1.next>=lst2.next){

 int result = lst1.next +lst2.next;

   return result;}

else {return lst.next;}

  } 

 }
```


















# Aufgabe 4a)
```java
public interface Foo{

public Integer apply(List<Integer> lst,Integer x);

}

public class MyFoo implements Foo{

 public Integer apply(List<Integer> lst, Integer x){

return Math.Max(lst.get(0), x);

//Alternativ =

return lst.get(0)>x? lst.get(0) : x; 

   }

 }
```












# Aufgabe 4b)
```java
public Interface Bar <T> {

public boolean apply(T a, T b);

 }

public class Mybar implements Bar<Integer>{

public boolean apply(Integer a, Integer b){

return a<b; 

}

 }
```















# Aufgabe 4c)

```java
public static BiFunction<Integer,Integer,List<Integer>> foobar(List<Integer> a,Integer b, Bar bar, Foo foo){

return (x,y)-> {

if(a.get(0) <=y && b >= x){

Arrays.asList(bar.apply(a,x), foo.apply(b,y))

    }

if(a.get(0)<=x && b>=y){

Array.asList(bar.apply(a,y),foo.apply(b,x));

 }

else{

throw new RunTimeException("no overlap");

}

}   

}

X.foobar(Arrays.asList(1,2,3),7-> (lst,x) ->Math.max(lst.x)-> (a,b)-> a<b? a:b;)
```


























# Aufgabe 5a)
```java
public static String[] foobar(String[] a, String[] b){

   int index = 0;

   int länge = a.length <b.length? a.length : b.length;

for(int i = 0; i<länge; i++){

if(a[i],equals(b[i])){

index +=2;

}

 }

String[] result = new String[index];

int resultIndex = 0;

for(int i = 0; i<länge; i++){

    if(a[i].equals(b[i])){

   result[resultIndex] = a[i].toLowerCase;

   result[resultIndex+1] = a[i].toUpperCase;

 reultIndex +=2;

   }

return result;

 }

 }
```













# Aufgabe 5b)
```java
public static String[] foobar(String[] a, String[] b, int index, int resultIndex){}

public int fillIndex(String[] a, String[] b,int i){

if(i == 0){

return 0;

}

}

public String[] resultind (String[]a, String b[]){

}
```










