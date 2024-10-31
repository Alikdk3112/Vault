
# Aufgabe 1 a)
```java 
public interface Abc <M extends Exception, N extends Object>{

public N func(Function<M,N> fct, M exc);

default public <T extends Number> void def (Collection<? super Number> x, List<? extends Number> y, T t){

   if(y.isEmpty()){

      x.add(t);

} 

   else{

       x.add(y.get(0));

}

```


# Aufgabe 1b)

```java
public abstract ClassA// M extends Number,N extends Object
implements Abc<M,N>, ActionListener{

 public N func (Function<M,N> fct, M exc){

//return vergessen
fct.apply(exc);

}
```

- Da es ein generisches Interface erbt, ist ClassA auch generisch, gleiche Parameter wie ActionListener
# Aufgabe 1c)

```java
public classB // 1. M extends Exception,N extends Object
extends ClassA {

private long when;

  public void actionPerformed(ActionEvent event){

            when = event.getWhen;

}

}
```
- gleich wie bei ClassA, generisch muss mitvererbt werden

# Aufgabe 2 a)


```java
// Exc2 extends Exception

// Exc2(char c);

public class Exc3 extends Exc2 {

public Exc3(String str){

super( ((str != null) && (str.length()>=1)) ? str.charAt(0) : '0' );

}

}
```
- Klammern benutzen beim ternären Operator
# Aufgabe 2 b)
```java
public static byte m(String s, Number n) throws Exc1, Exc2{

   if (s == null) {

      throw new Exc1();

   }

if (s.equals("FOP")){

throw new Exc2('m')

}

if (n != 0 && n instanceof Integer){

    if (n <Byte.MaxValue && n>Byte.MinValue){
// casting selber machen mit Integer
byte result = (byte) n;

return result;

}

else {

return 0;

}

throw new Exc3("FOP");

}

}
```
- Casting hier falsch, lieber sicher gehen und extra casten


# Aufgabe 2c)
```java
public byte m2 (byte b) throws Exc3{

   try{

   X.m("AuD", 357);  

   }

catch( Exc3 e){

 return b;

}

catch(Exception e){

throw new Exc3("m2");

}

return X.m;

}

```


# Aufgabe 3a)

``` java
public ListItem<Integer> foo(
ListItem<Integer> lst1,ListItem<Integer> lst2){

if (lst1 == null && lst2 == null){

  return null;

}

if (lst1 == null){

return bar(lst2,0);

}

if (lst2 == null){

return bar(lst1,0);

}

else {

returnfoo(lst1.next,lst2.next);}

}

public ListItem<Integer> bar (ListItem<Integer> lst, int accu){

if(lst == null){

return null;

}

else{

ListItem<Integer> tmp = new ListItem<>();

tmp.key = lst.key+accu;

tmp = lst;

bar(lst.next,accu+lstkey); 

}

}
```

 - Methode cons selber erstellen
```java
 private ListItem<T> cons(T num, ListItem<T> rest){
 // neues erstellen
 ListItem<T> item = new ListItem<Integer>();

item.key = num;
item.next = rest;

return item;
 }
```

# Aufgabe 3 b)



```java
public ListItem<Integer> foo( ListItem<Integer> lst1, ListItem<Integer> lst2){

}

public ListItem<Integer> bar (ListItem<Integer> lst, int accu){

if(lst == null){

   return null;

}

else{

ListItem<Integer> p = new ListItem<>();

    p = lst.next;

while(p != null){

p= p.next;

ListItem<Integer> tmp = new ListItem<>();

tmp.key = lst.key;

}

}

}
```
- Bar:
1. head und tail erstellen
2. pointer normal
3. accu kopieren
4. while schleife
5. accuCopy dem key zuweisen
6. if anweisung für head


# Aufgabe 4a)

```java
//foobar: number;number;number;number;boolean->(boolean)
//foo:    Number;list->Number
//bar:    Number,Number,Number->boolean



public interface Foo{

public Integer apply(Integer a, List<Integer> lst);

}

public class MyFoo implements Foo{

public Integer apply(Integer a, List<Integer> lst){

return a.intValue() * lst.get(0).intValue();
}
}
```
# Aufgabe 4b)

```java

```

# Aufgabe 4c)

```java

```
# Aufgabe 5 a)
.
```java
public int[] foobar(int[] a){
int index = 0;
//durchgehen
for (int i = 0 ; i<a.length;i++){
if(a[i] == i || a[i] == -i){
index++;
}

}
int[] result = new int[index];
int resultIndex = 0;

for (int i = 0; i < a.length; i++)
if (a[i] == i){
result[resultIndex] = a[i];
resultIndex++;

}
  }
 return result;
```



# Aufgabe 5b) (Array rekursiv)


```java

public static int[] foobar(int[] a){

int[] result = new int[foo(a,0)];

}

public static int foo(int [] a, int index){
if(index == 0){
return 0;
}

if(a[i]==a[i+1]){
index+1;
}
1+foo(a,index+1);

}

public static void bar(int[]a, int[] result, int aIndex, int resultIndex){

if(aIndex == a.length)
return;

if()

}

```