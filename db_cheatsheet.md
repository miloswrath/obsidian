>What to cover
>- Normalization/FDs x
>- Query processing x 
>- Procedure syntax
>- constraint/trigger syntax
>- transactions?

***FD Notes***
---
**Partial Dependency** ~ (*A*, B) :LiArrowRight: C  *Where A is a PK thus B isn't needed*
**Transitive Dependency** ~ A :LiArrowRight: B AND B :LiArrowRight: C thus indirectly A :LiArrowRight: C
**1NF** is individual items in cells, **2NF** is remove partials, **3NF** is remove transitive, **BCNF** requires any determinant to be a candidate key

***Query Processing***
---
`WHERE a = x` ~ $T(R)*\cfrac{1}{V(attr)}$
`WHERE A > x` ~ $T(R) * \cfrac{(val - min)}{(max - min)}$
`AND` (Independent) $\approx 10000 * (\cfrac{30-1}{126-1} * \cfrac{1}{9500}) \approx 0.244$
`AND` (Overlap)  $\approx 10000 * min[\cfrac{30-1}{126-1}, \ \cfrac{1}{9500}] \approx 1.053$
`OR` ~ just add the estimates
`Cartesian Join` $T(1)*T(2)$

***Procedures***
---
General Syntax:
```SQL
DELIMITER //
CREATE PROCEDURE <name>
IN <param>
OUT <param>
BEGIN 
/* IN params need to be unique from attributes
out params are */
SELECT <attr or agg> INTO
<end of the actual code>;
END //
```

***Transaction***
---
***To create a precedence graph***:
1. For each transaction add a node.
2. Write an array from $T_i \rightarrow T_j$ if:
	- $T_J$ reads a value after it's written by $T_i$
	- $T_j$ writes a value after its been written by $T_i$
	- $T_j$ reads a value after it's been written by $T_i$ 
3. If there is a cycle for any two nodes, it is not a conflict serializable transaction

