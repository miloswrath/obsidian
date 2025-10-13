## Question 1
---

*(a) Actors who acted only in horror (Relational Algebra)*

$$
H \;=\; \pi_{\text{actorid}}\!\left(\,\text{Cast} \;\bowtie_{\text{Cast.mid}=\text{Movies.mid}}\; \sigma_{\text{genre}='horror'}(\text{Movies})\right)
$$

$$
N \;=\; \pi_{\text{actorid}}\!\left(\,\text{Cast} \;\bowtie_{\text{Cast.mid}=\text{Movies.mid}}\; \sigma_{\text{genre}\neq'horror'}(\text{Movies})\right)
$$

$$
\textbf{Answer} \;=\; H \;-\; N
$$

---

*(b) SQL — Average sentiment for each genre*

```sql
SELECT
  genre,
  AVG(sentiment) AS avg_sentiment
FROM Movies
GROUP BY genre
ORDER BY genre;

```

## Question 2
---

```sql
-- Students with the largest score spread (max - min) across all their exams
SELECT student  
FROM Exams  
GROUP BY student  
HAVING MAX(score) - MIN(score) >= ALL(  
SELECT MAX(score) - MIN(score)  
FROM Exams  
WHERE score IS NOT NULL  
GROUP BY student
```

## Question 3
---

**C**

## Question 4
---

![[Pasted image 20251010212322.png]]

## Question 5
---
![[Pasted image 20251010213007.png]]
> Assumes that a salesperson is still considered an employee thus creating a sublass salesperson with its own recursive relationship manages.

## Question 6
---

```SQL
CREATE TABLE Client (  
UserID INT PRIMARY KEY,  
Tier VARCHAR(20) );  
CREATE TABLE Machine (  
Address VARCHAR(40) PRIMARY KEY,  
Region VARCHAR(50) );  
CREATE TABLE InteractsWith (  
TotalTime FLOAT,  
UserID INT REFERENCES Client,  
Address VARCHAR(40) REFERENCES Machine NOT NULL,  
PRIMARY KEY (UserID, Address) );
```
