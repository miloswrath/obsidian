## Question 1
---
#### 1NF
---

**Books**

> Books is in 1NF because all attributes contain atomic values — one accession number, one ISBN, one title, one author, and one publisher per row. Even though multiple rows may share the same ISBN (representing multiple physical copies), each field holds a single value, which satisfies the definition of 1NF.

**Users**

> Users is also in 1NF because every attribute contains a single value. No attribute contains repeating groups or multi-valued data. If a user belonged to multiple departments, that relationship would need to be represented through multiple tuples or a separate relation, since storing multiple deptids in one cell would violate 1NF.


#### 2NF
---

**Books**
- `accessionno⁺ = {accessionno, isbn, title, author, publisher}`
    
- So `accessionno` is a **candidate key** (single attribute)
    

> Books is in 2NF because its candidate key is a single attribute (accessionno). Since there is no composite key, there can be no partial dependency, and no non-key attribute depends on a proper subset of the key. Therefore, 2NF is automatically satisfied.

**Users**
From FDs:

- `userid → name, deptid`
    
- `deptid → deptname`
    
- `{userid}⁺` gives all attributes → `userid` is a **candidate key**
    

Since `userid` is a **single attribute key**, same rule applies.

> Users is also in 2NF because userid is a single-attribute candidate key. Since the key is not composite, no proper subset exists, so partial dependencies are not possible. Therefore, 2NF holds.

#### 3NF
---

**Books**
```
Books(accessionno, isbn, title, author, publisher)
FDs:
  accessionno → isbn
  isbn → title
  isbn → author
  isbn → publisher
  ```

*Violation*
  `isbn → {title, author, publisher}`

*Fix*
> Create a table with the violation
```
BookInfo(isbn, title, author, publisher)
```
> Keep a table where key still determines the determinant of the violatoin
```
BookCopy(accessionno, isbn)
```

**Users**
```
Users(userid, name, deptid, deptname)
FDs:
  userid → name, deptid
  deptid → deptname
```

*Violation*
  `deptid → deptname` (deptid not a superkey)

*Fix*
> Create a table with violation
```
Department(deptid, deptname)
```

> Remove deptname from users
```
Users(userid, name, deptid)
```
 
**Final Justification**
> To remove the transitive dependencies, the Books relation is decomposed into BookCopy(accessionno, isbn), where accessionno is the key, and BookInfo(isbn, title, author, publisher), where isbn is the key. In both relations, the determinant of every FD is a key, so both are in 3NF.

> Similarly, Users is decomposed into User(userid, name, deptid) and Department(deptid, deptname). userid and deptid are keys in their respective tables, so all FDs now have a superkey determinant and the schema is in 3NF.

#### BCNF
---

To check BCNF, every functional dependency $( X \rightarrow Y )$  must have  $( X )$ as a superkey.
If a determinant is not a superkey, the relation must be decomposed into:
- $( R_1 = X \cup Y )$
- $( R_2 = R \setminus (Y \setminus X))$

---

#### **Books**

**BookCopy(accessionno, isbn)**
- FD: accessionno → isbn  
- accessionno is a key for this relation  
**Determinant is a superkey → BCNF holds**

**BookInfo(isbn, title, author, publisher)**
- FD: isbn → title, author, publisher  
- isbn is a key for this relation  
**Determinant is a superkey → BCNF holds**

---

#### **Users**

**User(userid, name, deptid)**
- FDs: userid → name, deptid  
- userid is a key for this relation  
**Determinant is a superkey → BCNF holds**

**Department(deptid, deptname)**
- FD: deptid → deptname  
- deptid is a key for this relation  
**Determinant is a superkey → BCNF holds**

---

All decomposed relations satisfy BCNF. Each join is lossless because the common attribute in each decomposition (isbn or deptid) is a key in one of the resulting relations.


## Question 2
---
