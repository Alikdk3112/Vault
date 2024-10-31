```java
public static int[] foobar(int[] a){
int[] result = new Array[a.length-1];
int resultIndex = 0;
for (int i = 1; i<a.length-1;i++){

result[resultIndex]= a[i]+a[i-1];
resultIndex++;

}
return result

}
```