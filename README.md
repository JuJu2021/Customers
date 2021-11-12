# Customers
Leveraging my SQL skills to extract and analyze data from various tables in the Maven Movies database to answer the underwriters' questions.
/* Question 1 We will need a list of all staff members, inlcuding their fisrt and last names, email addresses and the store identification number where they work.
SELECT 
first_name,
last_name,
email,
store_id
FROM mavenmovies.staff;


/*Question 2 We will need seperate counts of inventory items held at each of your two stores.
Select
Store_id,
COUNT(inventory_id) AS 'count of inventory'
FROM inventory
GROUP BY store_id


/* Question 3 We will need a count of active customers for each of your stores. 
Select
Store_id,
COUNT(customer_id) AS 'no of active customer'
FROM customer
WHERE active = 1
GROUP BY store_id


/* QUESTION 4 We will need you to provide a count of all customer email addresses stored in the database.
SELECT
	COUNT(email) AS 'no. of email addresses'
FROM customer


/* QUESTION 5 Please provide a count of unique film titles you have in inventory at each store and then provide a count of the unique categories of films you provide.
SELECT
	store_id,
    	COUNT(DISTINCT film_id) AS 'no. of unique films'
FROM inventory
GROUP BY store_id

SELECT
	 COUNT(category_id) AS 'no of categories'
FROM category


/* QUESTION 6 Please provide the replacement cost for the film that is least expensize to replace, the most expensive to replace and the average of all films you carry.
SELECT
	MIN(replacement_cost) AS least_expensive_replacement_cost,
    	MAX(replacement_cost) AS most_expensive_replacement_cost,
    	AVG(replacement_cost) AS avg_replacement_cost
FROM film


/* QUESTION 7 Please provide the average payment you process, as well as the maximum payment you have processed.
SELECT
	MAX(amount) AS 'maximum payment processed',
    	AVG(amount) AS 'avg payment processed'
FROM payment


/* QUESTION 8 Please provide a list of all customer identification values, with a count of rentals they have made all-time, with your highest volume customers at the top.
SELECT
	customer_id,
    	COUNT(rental_id) AS 'no. of rentals'
FROM rental
GROUP BY customer_id
ORDER BY COUNT(rental_id) DESC
