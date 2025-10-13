## Question 1
---

*Advantages*
1. Reduced redundancy  
2. Increased data consistency  
3. Integrative view of data (enhanced sharing capabilities)  
4. Improved data integrity  
5. Tighter, granular, and improved security  

*Disadvantages*
1. Costs more  
2. Requires significant computing resources  
3. Increased complexity  
4. Requires skilled Database Administrator  
5. Centralized failure can severely impact access  

## Question 2
```sql
-- Find the median item when each value is unique
SELECT item
FROM LList
WHERE position = (
  SELECT (COUNT(*) + 1) / 2
  FROM LList
);
```

```SQL
-- Find the mode, i.e., the most frequently occurring item
SELECT item
FROM LList
GROUP BY item
ORDER BY COUNT(*) DESC
LIMIT 1;
```

## Question  3
```SQL
-- 3.1  DDL (with keys + constraints)

-- Assumptions (typical for this schema):
-- - Primary key for Union_Members is (m_name).
-- - A member can vote at most once per proposition, so Casted_Votes PK is (p_no, name).

CREATE TABLE Union_Members (
  m_name  VARCHAR(20) PRIMARY KEY,
  status  VARCHAR(10) NOT NULL,
  CONSTRAINT chk_um_status
    CHECK (status IN ('permanent','elected'))
);

CREATE TABLE Casted_Votes (
  p_no  INT NOT NULL,
  name  VARCHAR(20) NOT NULL,
  vote  VARCHAR(10) NOT NULL,
  CONSTRAINT pk_casted_votes
    PRIMARY KEY (p_no, name),
  CONSTRAINT fk_casted_votes_member
    FOREIGN KEY (name) REFERENCES Union_Members(m_name),
  CONSTRAINT chk_vote_value
    CHECK (vote IN ('yes','no','no comment'))
);

-- 3.2  Approved propositions:
-- Rule: ≥ 11 'yes' votes AND no 'no' from any 'permanent' member.

SELECT
  v.p_no
FROM
  Casted_Votes v
JOIN
  Union_Members m
  ON m.m_name = v.name
GROUP BY
  v.p_no
HAVING
  SUM(CASE WHEN v.vote = 'yes' THEN 1 ELSE 0 END) >= 11
  AND
  SUM(CASE WHEN m.status = 'permanent' AND v.vote = 'no' THEN 1 ELSE 0 END) = 0
ORDER BY
  v.p_no;

-- 3.3  Permanent members and their veto ('no') counts, including zeros.

SELECT
  m.m_name,
  COALESCE(SUM(CASE WHEN v.vote = 'no' THEN 1 ELSE 0 END), 0) AS veto_count
FROM
  Union_Members m
LEFT JOIN
  Casted_Votes v
  ON v.name = m.m_name
WHERE
  m.status = 'permanent'
GROUP BY
  m.m_name
ORDER BY
  m.m_name;
```

## Question 4
> Needs to be done using visio