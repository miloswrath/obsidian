## What this covers
---
>The RA that gets ran and estimation of runtime and cardinality of common operations

## What is an RA plan?
---
Say we have
![[Pasted image 20251212162642.png]]
Then say we want to find **names of all students taking more than 3 courses**
```SQL
SELECT s.name, s.id, COUNT(*) AS course_count
FROM student s JOIN takes t
ON s.id = t.id
GROUP BY s.id, s.name
HAVING COUNT(*) > 3
```
**The accompanying RA plan is**
![[query processing 2025-12-12 16.30.07.excalidraw]]

> Because we can solve the same query multiple ways, there is always a better/best way to run these queries

## What's the point of RA?
---
>An RDBMS uses RA to find the most efficient way to solve a query
![[Pasted image 20251212164821.png]]

In the RA step, the RDBMS does what's called **Plan Enumeration**
![[Pasted image 20251212164926.png]]
> Finding the path of least resistance to find the final set of executable code


## Plan Enumeration
---
- Some queries can be expressed in different ways
- RA formulation enforces optimization
	- RA specifies order of operations
	- Order largely determines the efficiency of the query 
- **Simplifies queries and makes them faster**

## Query RA Plans
---

### Project
---
Only project what you need! 
![[Pasted image 20251212165531.png]]

### Project & Union
---
