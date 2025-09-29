## File Based Systems
- Requires a *collection of programs* - each communicate independently and store data locally
![[Pasted image 20250929160102.png]]
- Here, essentially the sales and contracts stuff each need their own application with their own file storage techniques, making connecting and reporting data from both simultaneously very hard
- Often a duplication of data
- Programs might be written in different languages so the files aren't easily accessible between apps

> **Data was defined in the application**
> **No fine grained access control**

## DBMS
- This resulted in the **Database Management System** or **DBMS**
![[Pasted image 20250929160420.png]]
- This allowed for a more versatile yet stable environment to share data between applications

*Includes*
• a security system  
• an integrity system  
• a concurrency control system  
• a recovery control system  
• a user-accessible catalogue.