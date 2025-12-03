## Part 1
---
> Functional Dependencies
> Beginning of Normal Forms

## What is Normalization?
---
> A technique to produce the best set of relations that support the requirements of stakeholders

*This ensures*:
- Users have easy access
- Storage required is minimal
- *minimal* number of attrs necessary
- semantically close attributes are grouped together
- *minimal* redundancy

## How does Normalization fit?
---
You typically start with the requirements from the user which are then transformed into a **data dictionary**. 
From this, there are essentially two approaches to creating relations:
1. Top down - ER modeling
	- Start at a high level of relations and their attributes
	- Typically requires normalization as a **validation technique** afterwards
2. Bottom up - Normalization
	 - This technique uses the data dictionary and goes straight to the normalized form, skipping any top down modeling

