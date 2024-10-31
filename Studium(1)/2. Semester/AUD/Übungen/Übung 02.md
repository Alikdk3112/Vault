# Ali Kodak - Gruppe 14


## H1

a)

|     |     |     |     |     |
| --- | --- | --- | --- | --- |
| 8   |     |     |     |     |
| 8   | 7   |     |     |     |
| 8   | 7   | 6   |     |     |
|     | 7   | 6   |     |     |
|     |     | 6   |     |     |
|     |     | 6   | 7   |     |
|     |     | 6   | 7   | 2   |
|     |     |     | 7   | 2   |

b)
Stack:

| R   | E   | G   | A   | L   | E   |
| --- | --- | --- | --- | --- | --- |
| R   | E   | G   | A   | L   |     |
| R   | E   | G   | A   |     |     |
| R   | E   | G   | A   | X   |     |
| R   | E   | G   | A   |     |     |
| R   | E   | G   |     |     |     |
| R   | E   | G   | E   |     |     |
| R   | E   | G   | E   | N   |     |

c)
`new (S,n)`
```java
S.A[] = ALLOCATE(n);
S.top = -1;
S.memsize = n;
```
`push(S,k)`