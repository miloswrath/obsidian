### *FDs*
---
**Partial Dependency** ~ (*A*, B) -> C  *Where A is a PK thus B isn't needed*
**Transitive Dependency** ~ A -> B AND B -> C thus indirectly A -> C
**1NF** is individual items in cells, **2NF** is remove partials, **3NF** is remove transitive, **BCNF** requires any determinant to be a candidate key

### *Query Processing*
---
`WHERE a = x` ~ $T(R)*\cfrac{1}{V(attr)}$
`WHERE A > x` ~ $T(R) * \cfrac{(val - min)}{(max - min)}$
`AND` (Independent) $\approx 10000 * (\cfrac{30-1}{126-1} * \cfrac{1}{9500}) \approx 0.244$ ~~ *Muliply the estimates*
`AND` (Overlap)  $\approx 10000 * min[\cfrac{30-1}{126-1}, \ \cfrac{1}{9500}] \approx 1.053$ ~~ Take the minumum of the estimates
`OR` ~ just add the estimates
`Cartesian Join` $T(1)*T(2)$

### *Procedures*
---
General Syntax:
```SQL
DELIMITER //
CREATE PROCEDURE <name>
	IN <param>
	OUT <param>
BEGIN 
	/*
	IN params need to be unique from attributes
	out params are 
	*/
	SELECT <attr or agg> INTO
	<end of the actual code>;
END //
```

### *Transactions*
---
***To create a precedence graph***:
1. For each transaction add a node.
2. Write an array from $T_i \rightarrow T_j$ if:
	- $T_J$ reads a value after it's written by $T_i$
	- $T_j$ writes a value after its been written by $T_i$
	- $T_j$ reads a value after it's been written by $T_i$ 
3. If there is a cycle for any two nodes, it is not a conflict serializable transaction

**Lost Update** ~ One transaction overwrites another transaction before it's committed
**Uncommitted Dependency** ~ Transaction accesses another transactions writes before its committed ( and its usually rolled back afterwards )
**Inconsistent Analysis** ~ One $T$ reads  many values but some are overwritten by another before committing

### *Triggers*
---
```SQL
DELIMITER |
CREATE TRIGGER <name>
AFTER <insert? update?> ON <table_name>
FOR EACH ROW
BEGIN 
	code;
END |
DELIMITER ;
```

