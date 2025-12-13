## Security Overview Goals
---
![[Pasted image 20251213121052.png]]
 **What does DB security encompass?**
 *Protect sensitive data from*:
 - unauthorized disclosure
 - unauthorized modification
 - DoS attacks
*Security Controls*:
- Security policy
- Access control models
- Privacy problems
- Fault tolerance & recovery
- Auditing & intrusion detection

## Access Control
---
>Ensures that all _Direct Accesses_ are authorized

- Protects against accidental and malicious threats
- Regulates *read, write and execution* 
*Requires*
- Proper user authentication
- Information specifying access rights

**Subject**
- Active entity that requests acess
	- e.g. user or program
**Object**
- Passive entity accessed by subject
	- e.g. record, relation, file
**Access Right** 
- How a subject is allowed to access an object
	- e.g. subject *s* can read *o*

## Access Control Policies
---
[[#Discretionary Access Control]]
[[#Mandatory Access Control]]
[[#Role-Based Access Control]]

### Discretionary Access Control
---
>Access rights to objects are controlled for each subject

- (subject, object, rwx?)
- User-based policy
- **Grant and Revoke**
**Problems**
- Propogation of access rights
- Revocation of propogated access rights
![[security 2025-12-13 13.11.47.excalidraw]]
#### DAC ACMs
---
- Security Through Views
- Stored Procedures
- Grant & Revoke
- Query Modification
##### Security Through Views
---
>Assign rights to access predefined views

**EX**
```SQL
CREATE VIEW OutstandingStudent
AS SELECT name, course, grade
FROM STUDENT
WHERE grade > B
```
Then give users access to read this 