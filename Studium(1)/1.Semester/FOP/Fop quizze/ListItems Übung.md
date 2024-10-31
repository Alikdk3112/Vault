# [[Altklausur Sose 2021]]


# Frage 13


```java
public void foo(ListItem<T> lst1,ListItem<T> lst2, ListItem<T> tail){

if(lst1 == null || lst2 == null){
return;

}
ListItem<T> p1 = new ListItem<T>();
ListItem<T> p2 = new ListItem<T>();
p1 = lst1;
p2 = lst2;

(while p1 != null && p2 != null){
if(p1.key.equals(p2.key)){
tail = tail.next
tail = p.key;



 }


p2 = p2.next;
p1 = p1.next;
  }

}

```

[[Altklausur Sose22]]


```java 

public void foo(ListItem<T> lst, ListItem<T> tail){
ListItem<T> p = new ListItem<T>();
p = lst;
if(lst == null){
return;
}
while(p != null){
ListItem<T> tail.next = new ListItem<>();
ListItem<T> tmp = new ListItem();

tail.key =p.next.key ; 
tail = p.next;
tail.next.key = p.key
tail.next = p;
p = p.next.next;
 
  }


 }

```

```java

public List<T> foo(List<T> lst){
Iterator it = lst.iterator();
result = new LinkedList<T>();
while(it.hasNext){
T key = it.next();
resi

}


}

```

# [[Altklausur WiSE 22]]

Frage 8 
```java
public ListItem<T> foo(){

}

public ListItem<T> bar(ListItem<T> lst){
ListItem<T> lstReversed = new ListItem<T>();

ListItem<T> p = lst;

while (p != null){
ListItem<T> tmp = new ListItem<T>();
tmp.key = p.next.key ;
tmp.next = p;
tmp = p.next;
lstReversed = tmp;
lstReversed.next = null;

p = p.next;

}

return lstReversed;
}
```