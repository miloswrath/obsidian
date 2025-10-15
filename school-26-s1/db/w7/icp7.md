## Question 3
---
Two tables R(A,B) and S(B,C)
`SELECT R.A FROM R, S WHERE R.B = S.B`
`SELECT R.A FROM R WHERE R.B IN (SELECT B FROM S)`

*First Query*
- Can have multiple values of R.A where R.B = S.B. so if 1 R.B value matches to two S.B values, then the R.A with that R.B will show up twice

*Second Query*
- the `SELECT B FROM S` only produces one value because it is a set operation, returns a set of matching values. so any values of R.A that has an R.B that matches to two values of S.B don't get duplicated.
- only unique values

*outputs of second will always be in the outputs of the first.*

ANSWER = C

> Moral - always think about duplicates on exam, edge cases will come up for sure. Never assume a perfect table.

## Question 4
---
 Hospital is weak entity because without a hospital, you cannot have rooms

Operation is many to many, many doctors, many patients, many rooms, all at once


## Question 6
---
```SQL
CREATE TABLE Client (
	userID, INT, PRIMARY,
	Tier, VarChar(10)
);

CREATE TABLE Machine (
	Address, VarChar(64), PRIMARY
	Region, VarCHar(15)
);

CREATE TABLE Interacts (
	userID, references(Client.userID)
	Address, NOT NULL, references(Machine.Address)
	TotalTime, NOT NULL
);
```

