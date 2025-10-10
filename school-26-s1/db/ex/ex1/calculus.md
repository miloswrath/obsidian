PRactice 

- ```
  SELECT DISTINCT s.staffno, s.fname, s.lname, COUNT(city) AS count
  FROM Staff s JOIN PropertyForRent p 
  ON s.staffno = p.staffno 
  JOIN Viewing v 
  ON v.propertyno = p.propertyno
  GROUP BY s.staffno
  HAVING count > 1
  ORDER BY s.staffno
