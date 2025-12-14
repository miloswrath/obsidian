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