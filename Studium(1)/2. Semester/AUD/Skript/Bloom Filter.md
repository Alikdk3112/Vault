Speicherschonend

## Beispiel: schlechte Passwörter vermeiden
1. Speichere schlechte Passwörter in Bloom-Filter
2. Prüfe, ob eingegebenes Passwort im Bloom-fILTER IST
Starke Passwörter, die fälschlicherweise dem Wörterbuch zugeordnet werden, sind ärgerlich, aber nicht sehr schlimm
![[Pasted image 20240624193017.png]]
### Anwendungen 
- NoSQL-Datenbanken: Abfragen für nicht-vorhandene Elemente
- Bitcoin, Prüfen von Transaktionen 
### Erstellen
Gegeben: 
- $n$ Elemente $x_{0},\dots,x_{n-1}$ beliebiger Komplexität
- $m$ Bits Speicher, üblicherweise in einem Bit-Array
- $k$ "gute" Hash-Funktionen $H_{0},\dots,H_{k-1}$ mit Bildbereich $0,1,\dots,m-1$
- Empfohlene Wahl: $k=\frac{m}{n} * \ln2$-->ergibt Fehlerrate von va $2^-k$, üblichwerweise $k=5,6,\dots 20$
`initBloom(X,BF,H) //H array of functions H[j], BF bit-array, X array of Objects`
```java
FOR i=0 TO BF.LENGTHS-1 DO BF[i] = 0;// initalise array with 0 entries
FOR i=0 TO X.length-1 DO
	FOR J=0 TO H.length-1 DO
		BF[H[J]](X[i]) =1;
```
- Initalisiere Array mit 0 Einträgen
- Schreibe für jedes Element in jede Bit-Position $H_{0}(x_{i}),\dots, H_{k-1}(x_{i})$ eine 1
![[Pasted image 20240624195126.png]]

### Suchen
`searchBloom(BF,H,y) // H array of functions H[j]`
```java
result = 1;
FOR j=0 TO H-length-1 DO
		result=result AND BF[H[J](y)];
return result;
```


![[Pasted image 20240624202226.png]]
#### Beispielrechnung
$n = 100.000$ Passwörter, je 10 ASCII-Zeichen
![[Pasted image 20240624201925.png]]
