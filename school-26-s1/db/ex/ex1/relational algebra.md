
>Relational Algebra is the mathematical foundation of relational databases.  
>It defines a set of operations on relations (tables) that produce new relations.

## Common Operations

### 1. Selection (σ)
- **Purpose**: Choose rows that satisfy a condition.
- **Example**: σ(age > 30)(Employees) → employees older than 30.

### 2. Projection (π)
- **Purpose**: Choose specific columns.
- **Example**: π(name, salary)(Employees) → only name and salary.

### 3. Union (∪)
- **Purpose**: Combine tuples from two relations (no duplicates).
- **Example**: Employees ∪ Managers.

### 4. Difference (−)
- **Purpose**: Tuples in one relation but not in the other.
- **Example**: Employees − Managers → employees who are not managers.

### 5. Cartesian Product (×)
- **Purpose**: Pair every tuple of one relation with every tuple of another.
- **Example**: Students × Courses → all student-course pairs.

### 6. Join (⨝)
- **Purpose**: Combine tuples from two relations based on a condition.
- **Example**: Students ⨝ (Students.course_id = Courses.id) Courses.

## Joins

#### 🔗 What are Joins?
Joins combine rows from two or more tables based on a related column between them. The main types of joins are:

- **INNER JOIN**
- **LEFT OUTER JOIN (LEFT JOIN)**
- **RIGHT OUTER JOIN (RIGHT JOIN)**
- **FULL OUTER JOIN**
- **CROSS JOIN**
- **SELF JOIN**
- **NATURAL JOIN**

---

#### 📘 Sample Tables

**Table: `Employees`**

| id  | name    | dept_id |
| --- | ------- | ------- |
| 1   | Alice   | 10      |
| 2   | Bob     | 20      |
| 3   | Charlie | NULL    |

**Table: `Departments`**

| dept_id | dept_name   |
| ------- | ----------- |
| 10      | HR          |
| 20      | Engineering |
| 30      | Sales       |

---

#### 1. 🔍 INNER JOIN

Returns rows **only where there is a match** in both tables.

```sql
SELECT e.name, d.dept_name
FROM Employees e
INNER JOIN Departments d ON e.dept_id = d.dept_id;
````

**Result:**

| name  | dept_name   |
| ----- | ----------- |
| Alice | HR          |
| Bob   | Engineering |

**Relational Algebra:**

```
σ(e.dept_id = d.dept_id)(Employees ⨝ Departments)
```

---

#### 2. 👈 LEFT OUTER JOIN

Returns **all rows from the left table**, and matching rows from the right. Fills with `NULL` when there's no match.

```sql
SELECT e.name, d.dept_name
FROM Employees e
LEFT JOIN Departments d ON e.dept_id = d.dept_id;
```

**Result:**

| name    | dept_name   |
| ------- | ----------- |
| Alice   | HR          |
| Bob     | Engineering |
| Charlie | NULL        |

**Relational Algebra:**

```
Employees ⟕ Departments
```

---

#### 3. 👉 RIGHT OUTER JOIN

Returns **all rows from the right table**, and matching rows from the left. Fills with `NULL` when there's no match.

```sql
SELECT e.name, d.dept_name
FROM Employees e
RIGHT JOIN Departments d ON e.dept_id = d.dept_id;
```

**Result:**

| name  | dept_name   |
| ----- | ----------- |
| Alice | HR          |
| Bob   | Engineering |
| NULL  | Sales       |

**Relational Algebra:**

```
Employees ⟖ Departments
```

---

#### 4. 🔁 FULL OUTER JOIN

Returns **all rows from both** tables. `NULL` fills where there's no match.

```sql
SELECT e.name, d.dept_name
FROM Employees e
FULL OUTER JOIN Departments d ON e.dept_id = d.dept_id;
```

**Result:**

| name    | dept_name   |
| ------- | ----------- |
| Alice   | HR          |
| Bob     | Engineering |
| Charlie | NULL        |
| NULL    | Sales       |

**Relational Algebra:**

```
Employees ⟗ Departments
```

---

#### 5. ❌ CROSS JOIN (Cartesian Product)

Returns every possible combination of rows from both tables.

```sql
SELECT e.name, d.dept_name
FROM Employees e
CROSS JOIN Departments d;
```

**Result:**

| name  | dept_name   |
| ----- | ----------- |
| Alice | HR          |
| Alice | Engineering |
| Alice | Sales       |
| Bob   | HR          |
| ...   | ...         |

**Relational Algebra:**

```
Employees × Departments
```

---

#### 6. 🔄 SELF JOIN

Joins a table with itself to compare rows.

```sql
SELECT a.name AS Emp1, b.name AS Emp2
FROM Employees a, Employees b
WHERE a.dept_id = b.dept_id AND a.id < b.id;
```

**Use Case:** Find pairs of employees in the same department.

---

#### 7. 🧬 NATURAL JOIN

Automatically joins tables on all columns with the same name.

```sql
SELECT *
FROM Employees
NATURAL JOIN Departments;
```

**Caution:** May unintentionally join on more than intended if column names overlap.

**Relational Algebra:**

```
Employees ⋈ Departments
```

(_with implicit condition on common attribute_)

---

## ✅ Summary Table

| Join Type        | Returns Rows When...               | Missing Matches Filled With |
| ---------------- | ---------------------------------- | --------------------------- |
| INNER JOIN       | Matching key in both tables        | Not included                |
| LEFT OUTER JOIN  | All from left + matches from right | NULLs on right              |
| RIGHT OUTER JOIN | All from right + matches from left | NULLs on left               |
| FULL OUTER JOIN  | All from both, match if possible   | NULLs on either             |
| CROSS JOIN       | All combinations                   | N/A                         |
| SELF JOIN        | Matches within same table          | N/A                         |
| NATURAL JOIN     | Matches on all shared column names | N/A                         |

---

## 📘 Relational Algebra Notation Refresher

|Operation|Symbol|Description|
|---|---|---|
|Selection|σ|Filters rows (like `WHERE`)|
|Projection|π|Selects columns|
|Cartesian Product|×|All combinations (like `CROSS JOIN`)|
|Union|∪|Combines rows (eliminates duplicates)|
|Difference|−|Rows in one but not in the other|
|Rename|ρ|Renames relations or attributes|
|Join|⨝|Matches based on a condition|
|Left Join|⟕|All from left, matches from right|
|Right Join|⟖|All from right, matches from left|
|Full Outer Join|⟗|All from both, match where possible|

---

> 💡 **Tip:** In SQL, always ensure your joins have appropriate keys or conditions to avoid accidental Cartesian products!


## Questions to ask Chat

*From the example problems in book*
- b - because we are selecting after the join, then this would be the equiovalent of an inner join on hotelNo?
- e - explain more about the semijoin and its notation, is the notation directional? how can I think about or visualize a semijoin?