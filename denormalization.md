## What/Why
---
*Heavily normalized tables have slow performance in large scale settings because the required number of joins and cross-table operations required goes up as we remove dependencies. There could also be a table with too many rows, so splitting tables again might help query performance.*

![[Pasted image 20251208090106.png]]

## When 
---
 Typically done when:
 - have large-scale schemas and a requirement of optimized query performance.
 - high-dimensional analyses 
 - dealing with few updates but many searches

## How
---
*There are 5 main ways to denormalize*
1. Collapsing tables - joining two entities with 1-1 relationship
2. Splitting tables (Horizontally/Vertically)
3. Pre-Joining
4. Adding redundant columns (reference data)
5. Derived attributes (perform aggregates as a trigger function)

### Collapsing Tables
---
![[denormalization 2025-12-08 10.09.14.excalidraw]]

### Splitting Tables
---
> Split tables one of two ways which accomplish different goals
#### Horizontal Split
---
**GOAL**: 
- Spreading rows out to exploit parallelism
- Reduce computational complexity of queries with `WHERE` clause
- Also might help with reducing downtime effects. 
	- e.g. one table for US one for UK, if US goes down UK is still up
*Diagram*
![[denormalization 2025-12-08 10.12.47.excalidraw]]
#### Vertical Splitting
---
- This is not typically used for **denormalization** but for normalization. Thus, we will not go further into this. 