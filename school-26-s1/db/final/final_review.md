## Written questions
![[final_review 2025-12-12 12.48.31.excalidraw]]

## Question 4
---
Problem Statement:  
- In a retail management database, the sales team needs a quick and reliable way to apply discounts to all products within a specific  category during promotional periods. Create a reusable stored procedure is required to automate the discount application process and update a log.  
- Tables:  
	- products ( product_id, name, category_id, price);  
	- discount_log (log_id, product_id, old_price, new_price, applied_on, applied_by);
```SQL
delimiter //

CREATE PROCEDURE category_discount_update
	/* 
	dec (float): Decimal to multiply the price by (e.g. 0.85)
	cat (int): category id 
	*/ 
	IN (p_dec FLOAT, p_cat INT)
begin
	INSERT INTO discount_log (product_id, old_price, new_price, applied_on, applied_by)
	SELECT
		product_id,
		price AS old_price,
		price * p_dec AS new_price,
		NOW() AS applied_on,
		"Procedure Bot" AS applied_by
	FROM products
	WHERE category_id = p_cat;

	UPDATE products
	SET price = price*p_dec
	WHERE category_id = p_cat;
end 
//
delimiter ;
```
