

# Divide & Conquer

## Fourier Transformation

### Idee 
![[Pasted image 20240730192957.png]]


### Polynom: Koeffizientendarstellung
![[Pasted image 20240730193250.png]]

`PolyEval(p,n,w)// p[] array of n entries`
```java
y=p[n-1];
FOR i=n-2 DOWNTO 0 DO y=y*w+p[i];
return y;
```
Laufzeit $\theta(n)$

![[Pasted image 20240730193310.png]]
`PolyMult(p,q,n)//p,q arrays of n entries`
```java
r=ALLOC(2n-1);
FOR k=0 TO 2n-2 DO
	r[k]=0;
	FOR J=0 TO k DO r[k]=r[k]+p[j]*q[k-j];
return r;
```
Laufzeit $\theta(n^2)$

![[Pasted image 20240730193555.png]]
![[Pasted image 20240730193633.png]]
![[Pasted image 20240730193656.png]]
![[Pasted image 20240730193714.png]]
![[Pasted image 20240730193731.png]]
![[Pasted image 20240730193748.png]]