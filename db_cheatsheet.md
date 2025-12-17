>What to cover
>- Normalization/FDs
>- Query processing
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
