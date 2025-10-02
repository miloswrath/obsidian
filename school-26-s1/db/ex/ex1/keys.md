## Some general notation
---

*Domain*
- A Set of allowable values for one or more attributes

*Degree*
- \# of attributes

*Cardinality*
- \# of tupes

## keys
---
### Quick Analogy

- **Super Key** → "Any way to uniquely identify a person" (passport + SSN + email + combo).
    
- **Candidate Key** → "The minimal IDs" (passport _or_ SSN _or_ email).
    
- **Primary Key** → "The one official ID you pick" (say, passport).
    
- **Alternate Key** → "The other possible IDs not picked" (SSN, email).
    
- **Foreign Key** → "Reference to someone else’s ID in another list" (passport number stored in a visa application).


**There are 5 types of keys** 
1. Super key
2. Candidate Key
3. Primary Key
4. Alternate Key
5. Foreign Key

*Super Key*
- Any set keys that can be used to uniquely identify a tuple
- Can be more than one key
- Every table must have at least 1
- May contain extra, unnecessary attributes

*Candidate Key*
- A minimal super key - no unnecessary attributes
- Every candidate key is a super key, but no redundancy
	-Example
	- `{RollNo}` → candidate key.
	    
	- `{Email}` → candidate key.
	    
	- `{RollNo, Name}` is **not** a candidate key, because `Name` is unnecessary.

*Primary Key*
- The candidate key chosen by the database designer to identify rows
- Only one per table

*Alternate Key*
- Candidate keys that are not selected to be primary keys

*Foreign Key*
- An attribute in one table that refers to the *primary key* in another, creating a relationship