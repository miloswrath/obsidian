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

## Redundancy and Update Anomalies
---
> Relations that have redundant data often suffer from update anomalies

Example ->
Staff(sID, sName, lName, pos, bNo, bAddress)
If we want to update the address for one branch, then it requires updating for all sIDs

but if:
Staff(sID, sName, ..., bNo) & Branch(bNo, bAddress)
Updating address in Branch solves that issue

## Properties of Decomposition
---
*Lossless-Join*
- Able to find any instance of the whole relation by joining two smaller relations

*Dependency Preservation*
- Enforcing the same constraint that was on the original relation by enforcing it on the two smaller relations

## Functional Dependencies
---
> Specifies the direction of 1-1 relationships

For example:
	A and B have relation R
	If: B is functionally dependent on R (denoted $A \rightarrow B$)
		it is said that each value of A in R is associated with exactly one value B in R
### Relation: **Students**
| SID | Name  | Major |
|-----|--------|--------|
| 101 | Alex   | CS     |
| 102 | Bri    | Biology|
| 103 | Casey  | CS     |

#### Example FD
**SID → Name, Major**  
Each `SID` uniquely determines exactly one `Name` and one `Major`.

#### Valid FD Check
| SID | Name |
| --- | ---- |
| 101 | Alex |
| 101 | Alex |
← violates `SID → Name` (same SID gives two Names)
#### FD Violation
| SID | Name  |
| --- | ----- |
| 101 | Alex  |
| 101 | Jamie |
← violates `SID → Name` (same SID gives two Names)

### Diagrams
![[Pasted image 20251203113946.png]]

### Full Functional Dependency
---
> The set of determinants should be as small as possible

For example if:
	R(A,B,C) and A,C $\rightarrow$ B
	If C is not needed to functionally determine B then this is **NOT** FFD (called **partial dependency**)
	However if A,C is needed, then it is
#### Example Partial Dependency
---
![[Pasted image 20251203114442.png]]
Because `branchNo` can be determined by staffNo, then staffNo, sName is a partial dependency
## Transitive Dependencies
---
> In normalization, you usually try to remove partial dependencies first, but *transitive dependencies* are typically what causes *update anomalies*

**Def**
If A :LiArrowRight: B and B :LiArrowRight: C
then A :LiArrowRight: C, where A is not functionally dependent on B or C
^^ This is a little retarded so below is a better explanation

#### Better Explanation
A **transitive dependency** occurs when:

1. **A determines B** (A → B)
    
2. **B determines C** (B → C)
    
3. Therefore, **A indirectly determines C** through B (A → C)
    

This happens even though **C is not directly dependent on A**, and **A is not dependent on B or C**.

##### **Intuition**

A affects B, and B affects C — so A _passes its influence_ through B to determine C.

##### **Simple Example**

Relation: **Student(SID, Major, DeptOffice)**  
FDs:

- **SID → Major**
    
- **Major → DeptOffice**
    

Because SID determines Major, and Major determines DeptOffice:

➡️ **SID → DeptOffice** is a **transitive dependency**


> Essentially the problem from the beginning example
## PART 2
---
> Redefining Normalization
> Technique for optimizing a set of relations based on their FDs between attrs and their primary keys
> This is often done in a series of steps - called **Normal Forms**


### Identifying FDs
---
*Identifying FDs requires a semantic explanation of a relation and its attrs, typically done in conversation with stakeholders*
^^ For example:
For the following table, if we knew nothing about the functionality of these attrs and how they work together
![[Pasted image 20251203144550.png]]
We would have 
![[Pasted image 20251203144609.png]]
Because staffNo is obviously the primary key, and branchNo and bAddress FD each other
However 
**If `position` and `branch` determine `salary`** 
then we add 
![[Pasted image 20251203144741.png]]
^^ Thus we need to know more about how the data works in this instance to understand all FDs

### Identifying a Primary Key
---
> Once you have FDs, you need to choose a primary key
> This will include any non-standard integrity constraints 

From the FDs you identify the candidate keys, then select the most reasonable primary key.

To identify the primary key from candidate keys, find the minimal set of candidate keys that are determinants of all other attrs in that relation

## Process of Normalization
---
> The set of steps that lead to an optimized, robust, and secure database schema

*As you go through the steps of normalization, the relations become progressively more **restricted** which means they are **stronger**. They are also less vulnerable to update anomalies.*

### Normal Forms Visuals
---
*Hierarchy of Normal Forms*
![[Pasted image 20251203154219.png]]

*Process of Normalization*
![[Pasted image 20251203154323.png]]

### Normal Forms
---
> The following will describe and show the process of normalizing a database

#### Unnormalized Form (UNF)
---
This is the *rawest* state that a database can be in. 
- Contains 1 or more repesating groups.
- Essentially just transforming some raw mixed (input from forms, etc.) data into table format with columns and row.
*Example*
![[Pasted image 20251203154521.png]]

#### 1st Normal Form (1NF)
---
![[Pasted image 20251203154637.png]]
From the processes image, our first step is to remove repeating groups. But first, we must identify a key to uniquely identify all rows.

In the UNF example we had reapeating groups for each clientNo, cName :LiArrowRight: propertyNo, pAddress, ..., etc.

We can just make clientNo the key
![[Pasted image 20251203154849.png]]
Now we are in 1NF! Still very ugly and messy.



