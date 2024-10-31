```java
public static int[] foobar(int[] a){
int lenght = foo(a,0);
int[] result =new Int[length];
bar(a,0,result,0);
return result;

 
}


private static int foo(int[] a, int index){

if(!(index<a.length)){
return 0;
}
if(a[index] == index || a[index] == -index ){

return foo(a,index+1) +1;
}
return foo(a,index+1);

}

private static void bar(int[] a, int[] result, int index, int resultIndex){

if(!(index<a.length)){
return ;

}
if(a[index] == index || a[index] == -index ){
result[resultindex] = a[index]; 
resultIndex++;
}

bar(a,result,index +1,resultIndex)

```


```java
public static XXX foo(int[] a){

int amout = 0;

for (int i = 0; i < a.length; i++){

 if(a[2*i] >= a[2*i+1] ){

  amount++;

  }

   }

int[] result = new int[amount];

int resultIndex = 0;

for (int i = 0; i< a.length; i++){

if(a[2*i] >= a[2*i+1]){

result[resultIndex] = a[2*i];

 resultindex++;

   }

   }

return result;

 }
```

```java
public static int[] foo(int[] a){

int amount = bar(a, 0);

int[] result = new int[amount];

foobar(a,result,0);

return result;

}

private static bar(int[] a, int index){

if (!(a<a.length)){

   return 0;

    }

return bar(a,index+1) + (a[2*index] >= a[2*index+1])? 1: 0;

 }

private static void foobar(int a[], int[] result,int indexInA, int resultIndex){

if(!(a<a.length)){

   return;

  }

if(a[2*indexInA] >= a[2*indexInA]){

result[resultIndex] = a[2*indexInA];

resultIndex++;

  }

foobar(a,result,indexInA +1, resultIndex);

}
```

```java
public static String[] bar (String[] a, String[] b){

int amount = foo(a,b,0);

String result = new String[amount];

bar(a,b,result,0,0);

return result;

}

private static int foo(String[] a, String[] b,int index){

int cond = a.length < b.length? a: b;

if(!(index<cond)){

   return 0;

  }

return foo(a,b,index +1) + a[index].equals(b[index]) ? 2 : 0;

} 

private static void bar(String[] a, String[] b,String[] result, int indexInAandB,int resultIndex){

int cond = a.length < b.length? a:b;

if(!(indexInAandB <cond)){

return;

}

if (a[indexInAandB].equals(b[indexInAandB])){

result[resultIndex] = a[IndexInAandB].toLowerCase;

result[resultIndex +1] = a[IndexInAandB].toUpperCase;

resultIndex +=2;

} 

bar(a,b,result,indexInAandB +1, resultIndex);

}
```