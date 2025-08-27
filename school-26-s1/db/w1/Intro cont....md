## DBMS
- tool / collection to create or maintain dbs 
- located locally or remote server
- allow secure access and per user auth

## RDBMS 
- relational

##### advantages
- *reduced redundancy* (relations reduce duplication)
	- *sometimes redundancy is used for historical reporting*
	- updates made by one user are reflected for all users (*stateful*)
	- **Lower redundancy -> higher consistency**
- *consistency* - no making changes on `x1` that aren't reflected on `x2` if there is only `x1` 
	- consistency leads to integrity and accuracy
- *concurrency* - if multiple users are trying to change same value - must sort who gets to change it - not both at the same time
	- **must** come after consistency
- *sharing of data* - multiple users access with different roles to share and manipulate same data at the same time
- *integrity* - data should be semantically valid 
- *granular security* - access is role based
- *economy* - cheaper
- *performance*
- *backup recovery*
- *object reuse* - reuse functions
	- triggers
	- stored procedures
- *distributed*, *durabillity/uptime*, *query optimizations & indexes*

##### Disadvantages
- cost
- complexity
- resource requirements
	- DBA 
- low downtime but high impact 
	- always running



--- 