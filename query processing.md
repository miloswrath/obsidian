## What this covers
---
>The RA that gets ran and estimation of runtime and cardinality of common operations

## What is an RA plan?
---
Say we have
![[Pasted image 20251212162642.png]]
Then say we want to find **names of all students taking more than 3 courses**
```
SELECT s.name
FROM student s JOIN takes t
ON s.id = t.id
GROUP BY s.ID
HAVING 
```