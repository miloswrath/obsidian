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

