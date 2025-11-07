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
### Trigger 1
```SQL
-- Question 1

-- The price of all double rooms must be greater than £100



DELIMITER //



-- Before Insert 

DROP TRIGGER IF EXISTS room_price_bi// -- Cuz i screwed up a lot...

CREATE TRIGGER room_price_bi

BEFORE INSERT ON Room

FOR EACH ROW

BEGIN

  IF UPPER(NEW.type) IN ('D','DOUBLE') AND NEW.price <= 100.00 THEN

    SIGNAL SQLSTATE '45000'

      SET MESSAGE_TEXT = 'Double room price must be > 100';

  END IF;

END//



-- Before Update

DROP TRIGGER IF EXISTS room_price_bu//

CREATE TRIGGER room_price_bu

BEFORE UPDATE ON Room

FOR EACH ROW

BEGIN

  IF UPPER(NEW.type) IN ('D','DOUBLE') AND NEW.price <= 100.00 THEN

    SIGNAL SQLSTATE '45000'

      SET MESSAGE_TEXT = 'Double room price must be > 100';

  END IF;

END//



DELIMITER ;
```

### Trigger 2

```SQL
-- Prevent a guest from having overlapping bookings (any hotel/room)


DELIMITER //



DROP TRIGGER IF EXISTS booking_overlap_bi//

CREATE TRIGGER booking_overlap_bi

BEFORE INSERT ON Booking

FOR EACH ROW

BEGIN

  IF EXISTS (

    SELECT 1

    FROM Booking b

    WHERE b.guestNo = NEW.guestNo

      AND NOT (

        IFNULL(NEW.dateTo, '9999-12-31') < b.dateFrom

        OR IFNULL(b.dateTo, '9999-12-31') < NEW.dateFrom

      )

  ) THEN

    SIGNAL SQLSTATE '45000'

      SET MESSAGE_TEXT = 'Guest cannot have overlapping bookings';

  END IF;

END//



DROP TRIGGER IF EXISTS booking_overlap_bu//

CREATE TRIGGER booking_overlap_bu

BEFORE UPDATE ON Booking

FOR EACH ROW

BEGIN

  IF EXISTS (

    SELECT 1

    FROM Booking b

    WHERE b.guestNo = NEW.guestNo

      AND NOT (

        IFNULL(NEW.dateTo, '9999-12-31') < b.dateFrom

        OR IFNULL(b.dateTo, '9999-12-31') < NEW.dateFrom

      )

      -- exclude the row being updated (uses old PK)

      AND NOT (

        b.hotelNo = OLD.hotelNo

        AND b.guestNo = OLD.guestNo

        AND b.dateFrom = OLD.dateFrom

      )

  ) THEN

    SIGNAL SQLSTATE '45000'

      SET MESSAGE_TEXT = 'Guest cannot have overlapping bookings';

  END IF;

END//

DELIMITER ;
```

### Trigger 3
```SQL
-- Question 3

-- A booking cannot be for a hotel room that is already booked for any of the specified dates.



DELIMITER //



DROP TRIGGER IF EXISTS booking_room_overlap_bi//

CREATE TRIGGER booking_room_overlap_bi

BEFORE INSERT ON Booking

FOR EACH ROW

BEGIN

  IF EXISTS (

    SELECT 1

    FROM Booking b

    WHERE b.hotelNo = NEW.hotelNo

      AND b.roomNo  = NEW.roomNo

      AND NOT (

        IFNULL(NEW.dateTo, '9999-12-31') < b.dateFrom

        OR IFNULL(b.dateTo, '9999-12-31')   < NEW.dateFrom

      )

  ) THEN

    SIGNAL SQLSTATE '45000'

      SET MESSAGE_TEXT = 'Room is already booked for at least one of those dates';

  END IF;

END//



DROP TRIGGER IF EXISTS booking_room_overlap_bu//

CREATE TRIGGER booking_room_overlap_bu

BEFORE UPDATE ON Booking

FOR EACH ROW

BEGIN

  IF EXISTS (

    SELECT 1

    FROM Booking b

    WHERE b.hotelNo = NEW.hotelNo

      AND b.roomNo  = NEW.roomNo

      AND NOT (

        IFNULL(NEW.dateTo, '9999-12-31') < b.dateFrom

        OR IFNULL(b.dateTo, '9999-12-31')   < NEW.dateFrom

      )

      -- exclude the row being updated (use OLD PK + roomNo)

      AND NOT (

        b.hotelNo = OLD.hotelNo

        AND b.guestNo = OLD.guestNo

        AND b.dateFrom = OLD.dateFrom

        AND b.roomNo = OLD.roomNo

      )

  ) THEN

    SIGNAL SQLSTATE '45000'

      SET MESSAGE_TEXT = 'Room is already booked for at least one of those dates';

  END IF;

END//

```