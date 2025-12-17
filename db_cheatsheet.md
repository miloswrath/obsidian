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
`AND` (Independent) $\approx 10000 * (\cfrac{30-1}{126-1} * \cfrac{1}{9500}) \approx 0.244$
`AND` (Overlap)  $\approx 10000 * min[\cfrac{30-1}{126-1}, \ \cfrac{1}{9500}] \approx 1.053$
`OR` ~ just add the estimates
