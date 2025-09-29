# CS 4400: Database Systems - Assignment 1

## Problem 1

Assume relations R and S are union-compatible for union and intersection operations, with n and m tuples respectively (n, m ≥ 0). For part c, the selection condition C is arbitrary. For part d, assume the projection list L makes Π_L(R) compatible with S for the set difference operation.

### a) R ∪ S

Minimum number of tuples: $$\max(n, m)$$  
(Occurs when one relation is a subset of the other.)

Maximum number of tuples: $$n + m$$  
(Occurs when R and S have no tuples in common.)

### b) R ∩ S

Minimum number of tuples: $$0$$  
(Occurs when R and S have no tuples in common.)

Maximum number of tuples: $$\min(n, m)$$  
(Occurs when one relation is a subset of the other.)

### c) σ_C(R) × S

Let k be the number of tuples in σ_C(R), where $$0 \leq k \leq n$$.

Minimum number of tuples: $$0$$  
(Occurs when k = 0, i.e., no tuples in R satisfy C.)

Maximum number of tuples: $$n \times m$$  
(Occurs when k = n, i.e., all tuples in R satisfy C.)

### d) Π_L(R) − S

Let p be the number of distinct tuples in Π_L(R), where $$0 \leq p \leq n$$ (assuming R may have duplicates projected away).

Minimum number of tuples: $$0$$  
(Occurs when all tuples in Π_L(R) are also in S.)

Maximum number of tuples: $$p \leq n$$  
(Occurs when no tuples in Π_L(R) are in S; the exact max depends on duplicates in R but is at most n.)

## Problem 2

The queries are formulated in Tuple Relational Calculus (TRC) and Domain Relational Calculus (DRC). Assumptions: 
- All relations are as defined in the schema.
- For query 7, overdue books are those where dateDue < '2025-09-26' (using the current date provided).
- Queries return the specified attributes; existential quantifiers are used for joins.
- No nulls or additional constraints beyond the schema.

### 1. List all book titles.

#### Tuple Relational Calculus
$$
\{ b.title \mid Book(b) \}
$$

#### Domain Relational Calculus
$$
\{  t  \mid \exists i, e, y (\langle i, t, e, y \rangle \in Book) \}
$$

### 2. List all borrower details.

#### Tuple Relational Calculus
$$
\{ bor \mid Borrower(bor) \}
$$
(Returns entire borrower tuples: borrowerNo, borrowerName, borrowerAddress.)

#### Domain Relational Calculus
$$
\{  bn, bname, baddr  \mid ( bn, bname, baddr ) \in Borrower \}
$$

### 3. List all book titles published in the year 2012.

#### Tuple Relational Calculus
$$
\{ b.title \mid Book(b) \land b.year = 2012 \}
$$

#### Domain Relational Calculus
$$
\{  t  \mid \exists i, e ( i, t, e, 2012  \in Book) \}
$$

### 4. List all copies of book titles that are available for borrowing.

#### Tuple Relational Calculus
$$
\{ bc.copyNo \mid BookCopy(bc) \land bc.available = true \}
$$

#### Domain Relational Calculus
$$
\{  cn  \mid \exists i ( cn, i, true  \in BookCopy) \}
$$

### 5. List all copies of the book title Lord of the Rings that are available for borrowing.

#### Tuple Relational Calculus
$$
\{ bc.copyNo \mid BookCopy(bc) \land bc.available = true \land \exists b (Book(b) \land b.ISBN = bc.ISBN \land b.title = 'Lord of the Rings') \}
$$

#### Domain Relational Calculus
$$
\{  cn  \mid \exists i ( cn, i, true  \in BookCopy \land \exists e, y ( i, 'Lord of the Rings', e, y  \in Book)) \}
$$

### 6. List the names of borrowers who currently have the book title Lord of the Rings on loan.

#### Tuple Relational Calculus
$$
\{ bor.borrowerName \mid Borrower(bor) \land \exists bl (BookLoan(bl) \land bl.borrowerNo = bor.borrowerNo \land \exists bc (BookCopy(bc) \land bc.copyNo = bl.copyNo \land \exists b (Book(b) \land b.ISBN = bc.ISBN \land b.title = 'Lord of the Rings'))) \}
$$

#### Domain Relational Calculus
$$
\{ \langle bname \rangle \mid \exists bn, baddr (\langle bn, bname, baddr \rangle \in Borrower \land \exists do, dd, cn (\langle cn, do, dd, bn \rangle \in BookLoan \land \exists i, av (\langle cn, i, av \rangle \in BookCopy \land \exists e, y (\langle i, 'Lord of the Rings', e, y \rangle \in Book)))) \}
$$

### 7. List the names of borrowers with overdue books.

#### Tuple Relational Calculus
$$
\{ bor.borrowerName \mid Borrower(bor) \land \exists bl (BookLoan(bl) \land bl.borrowerNo = bor.borrowerNo \land bl.dateDue < '2025-09-26') \}
$$

#### Domain Relational Calculus
$$
\{  bname  \mid \exists bn, baddr ( bn, bname, baddr  \in Borrower \land \exists cn, do, dd ( cn, do, dd, bn  \in BookLoan \land dd < '2025-09-26')) \}
$$

### 8. For each book title with more than three copies, list the names of library members who have borrowed them.

#### Tuple Relational Calculus

$$
\{ bor.borrowerName \mid Borrower(bor) \land \exists bl (BookLoan(bl) \land bl.borrowerNo = bor.borrowerNo \land \exists bc (BookCopy(bc) \land bc.copyNo = bl.copyNo \land \exists b (Book(b) \land b.ISBN = bc.ISBN \land \exists bc1, bc2, bc3, bc4 (BookCopy(bc1) \land bc1.ISBN = b.ISBN \land BookCopy(bc2) \land bc2.ISBN = b.ISBN \land bc2.copyNo \neq bc1.copyNo \land BookCopy(bc3) \land bc3.ISBN = b.ISBN \land bc3.copyNo \neq bc1.copyNo \land bc3.copyNo \neq bc2.copyNo \land BookCopy(bc4) \land bc4.ISBN = b.ISBN \land bc4.copyNo \neq bc1.copyNo \land bc4.copyNo \neq bc2.copyNo \land bc4.copyNo \neq bc3.copyNo)))) \}
$$

#### Domain Relational Calculus
Similarly, express >3 copies via at least four distinct copyNo for the same ISBN.

$$
\{  bname  \mid \exists bn, baddr ( bn, bname, baddr  \in Borrower \land \exists cn, do, dd ( cn, do, dd, bn  \in BookLoan \land \exists i, av ( cn, i, av  \in BookCopy \land \exists t, e, y (\ i, t, e, y  \in Book \land \exists cn1, av1 ( cn1, i, av1  \in BookCopy \land cn1 \neq cn) \land \exists cn2, av2 ( cn2, i, av2  \in BookCopy \land cn2 \neq cn \land cn2 \neq cn1) \land \exists cn3, av3 ( cn3, i, av3  \in BookCopy \land cn3 \neq cn \land cn3 \neq cn1 \land cn3 \neq cn2) \land \exists cn4, av4 ( cn4, i, av4  \in BookCopy \land cn4 \neq cn \land cn4 \neq cn1 \land cn4 \neq cn2 \land cn4 \neq cn3))))) \}
$$