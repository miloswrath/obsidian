## Screenshots

### Question 1.2
---
![[Pasted image 20251117115657.png]]
![[Pasted image 20251117120012.png]]
***This passes because the update is made for Stack Books through the `Publisher` table. This is the table allowed from the trigger. Changes were also made for all Stack Books in the `Book` table as well (second screenshot)***

i![[Pasted image 20251117115737.png]]
***This update fails because the update to `editor_in_chief` is through the Book table. Because the trigger protects against updates to `editor_in_chief` in the Book table and only allows updates to the `Publisher` table, this fails. Error returns a useful message for usability***.

### Question 1.2
---
![[Pasted image 20251117115825.png]]
***This is just a test for the on-insert trigger in the `pubBook` table. This was not requested from the assignment PDF but useful for testing***.
