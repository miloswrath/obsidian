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

## Query RA Plans & Equivalences
---

### Project
---
Only project what you need! 
![[Pasted image 20251212165531.png]]

### Project & Union
---
![[Pasted image 20251212170051.png]]
* Make sure the **schema matches**
* *may not work with set difference or intersection*

### Select & Project
---
![[Pasted image 20251212170234.png]]
- Only if **C** references attrs in **A**

### Select & AND
---
>Remember: Select is not select in SQL

![[Pasted image 20251213105713.png]]
**C** and **d** are *Boolean*
*e.g.* - WHERE `a` = 5 AND b =  6


## Cardinality Estimation
---
Assume `University Database`
```
T(Student) = 10,000 
V(lastName) = 9,500 
V(major) = 10 
Range(credits) = [1, 126)
```
### WHERE Estimation (WHERE is an '=')
---
EX: 
```SQL
SELECT * FROM STUDENT 
WHERE lastname = 'Happy';
```
*How many tuples do we expect to be outputted?*
(*Assume distinct value are uniformly distributed*)
$T(R)*\cfrac{1}{V(attr)} = 10000 * 1/9500  \approx 1.05 \\ \text{   tuples}$
![[query processing 2025-12-13 11.09.33.excalidraw]]


### WHERE Range (WHERE is an inequality)
---
EX:
```SQL
SELECT * FROM STUDENT
WHERE credits < 30;
```
*How many distinct tuples? (same assumptions)*
$T(R) * \cfrac{(val - min)}{(max - min)} = 10000 * \cfrac{30 - 1}{126 - 1 } \approx 2320 \\ \text{   tuples}$
![[query processing 2025-12-13 11.14.19.excalidraw]]

### AND Estimation
---
**There are three different cases for the `AND` condition**
1. The tuples are *disjoint* - There are matches between two conditions
2. The conditions are *independent* there will be **multiple** estimates
3. The conditions *fully overlap* take the **minimum** of estimates
>It's usually best to assume independence unless you know otherwise

**If Independent**
Mutiple selectivity factors
$\approx 10000 * (\cfrac{30-1}{126-1} * \$