E-commerce business dataset containing end to end details about the customers, orders, products and sales was taken.
A schema with 4 tables was used for data analysis.
Below is the list of deductions drawn from this data which can be effectively utilized to make important business decisions.

--List of unique top customers with high spending rate--

SELECT DISTINCT(customer_name), c.gender, c.home_address, c.state, o.payment
FROM customers as c 
JOIN orders as o 
   ON (c.customer_id = o.customer_id) 
JOIN sales as s
   ON (o.order_id = s.order_id)
ORDER BY (payment) DESC


--User demographics and payment data (without duplicates) of the customers who've purchased atleast 1 product and spent more than 20000-

SELECT DISTINCT(customer_name), c.gender, c.home_address, c.state, o.payment
FROM customers as c 
JOIN orders as o 
   ON (c.customer_id = o.customer_id) 
JOIN sales as s
   ON (o.order_id = s.order_id)
WHERE (o.payment > 20000) and (quantity >= 1)

--Total sales revenue for the product "Dress" with the size "XS"-- 

SELECT p.product_name, SUM(s.total_price)
FROM products as p
JOIN sales as s
ON s.product_ID = p.product_ID
WHERE (p.product_name = "Dress") AND (p.size = "XS")

--Minimum number of products sold and minimum revenue made in the city "Walterland"-- 

SELECT MIN(o.payment), MIN(s.quantity)
FROM customers as c 
JOIN orders as o 
   ON (c.customer_id = o.customer_id) 
JOIN sales as s
   ON (o.order_id = s.order_id)
WHERE c.city = "Walterland"

--Number of female customers from the city Queensland--
SELECT COUNT("customer_name")
FROM customers
WHERE (gender= "Female") and (state= "Queensland")

--Total list of female customers along with their home address who've paid more than 10000--

SELECT c.customer_name, c.home_address
FROM customers as c
JOIN orders as o
ON c.customer_id = o.customer_id
WHERE (c.gender = "Female") and (o.payment > 10000)

--List of male customers (without duplicates) along with their home address who've paid more than 10000--

SELECT DISTINCT(c.customer_name), c.home_address
FROM customers as c
JOIN orders as o
ON c.customer_id = o.customer_id
WHERE (c.gender = "Male") and (o.payment > 10000)


--Total sales revenue for the product "Oxford Cloth" with the product type "Jacket"-- 

SELECT SUM(s.total_price)
FROM products as p
JOIN sales as s
ON s.product_ID = p.product_ID
WHERE (p.product_name = "Oxford Cloth") AND (p.product_type = "Jacket")










 