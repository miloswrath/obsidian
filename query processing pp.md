```
T(Q) = 2500  
V(Q,a) = 30  
V(Q,b) = 500  


T(R) = 6000  
V(R,a) = 60  
V(R,c) = 20  
V(R,d) = 40  


T(S) = 1000  
V(S,b) = 250  
V(S,d) = 100  
```
```SQL
SELECT *  
FROM R NATURAL JOIN S  
WHERE R.a = 22 AND S.b = 90
```

![[query processing pp 2025-12-13 21.50.20.excalidraw]]


Relations: **Q(a,b), R(a,c,d), S(b,d)**  
Stats:

- T(Q)=4000, V(Q,a)=40, V(Q,b)=800
    
- T(R)=9000, V(R,a)=90, V(R,c)=30, V(R,d)=60
    
- T(S)=1200, V(S,b)=300, V(S,d)=150
    

Query:

`SELECT * FROM R NATURAL JOIN S WHERE R.a = 10 AND S.b = 50;`

![[query processing pp 2025-12-15 12.41.13.excalidraw]]

## Problem 2

Relations: **A(x,y), B(y,z), C(z,w)**  
Stats:

- T(A)=5000, V(A,x)=100, V(A,y)=250
    
- T(B)=8000, V(B,y)=400, V(B,z)=200
    
- T(C)=3000, V(C,z)=150, V(C,w)=60
    

Query:

`SELECT * FROM A NATURAL JOIN B NATURAL JOIN C WHERE A.x = 7 AND C.w = 12;`
![[query processing pp 2025-12-15 12.51.28.excalidraw]]