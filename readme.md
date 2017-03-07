# SQL & Databases

How many users are there? 50 
* SELECT count(*) FROM users;

What are the 5 most expensive items? Small Cotton Gloves, Small Wooden Computer, Awesome Granite Pants, Sleek Wooden Hat, Ergonomic Steel Car
* SELECT title FROM items ORDER BY price DESC;

Whats the cheapest book? Ergonomic Granite Chair
* SELECT * FROM items WHERE category LIKE '%book%' ORDER BY price ASC;

Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address? Corinne Little
* SELECT * FROM addresses JOIN users ON addresses.user_id = users.id WHERE addresses.street LIKE '%6439%';

Do they have another address? 54369 Wolff Forges
* SELECT * FROM addresses JOIN users ON addresses.user_id = users.id WHERE users.first_name LIKE '%corrine%';

Correct Virginie Mitchells address to "New York, NY, 10108".
* SELECT * FROM users WHERE users.first_name LIKE '%Virginie%'; (id = 39)
* UPDATE addresses SET city='New York'WHERE user_id=39;
* UPDATE addresses SET state='NY'WHERE user_id=39;
* UPDATE addresses SET zip='10108' WHERE user_id=39;

How much would it cost to buy one of each tool? 467488
* SELECT SUM(price) FROM items;

How many total items did we sell? 100
* SELECT count(*) FROM items

How much was spent on books? 36
* SELECT count(*) FROM items JOIN orders ON orders.item_id = items.id WHERE category LIKE '%book%';

Simulate buying an item by inserting a User for yourself and an Order for that User.
* INSERT INTO users (id, first_name, last_name, email) VALUES (51, 'Julius', 'Williams', 'jmichaelcodes@gmail.com');
* INSERT INTO orders (id, user_id, item_id, quantity, created_at) VALUES (378, 51, 100, 1, '2017-03-06 02:15:00');

What item was ordered most often? Items 10, 46, and 65
* SELECT item_id, COUNT(item_id) AS Frequency FROM orders GROUP BY item_id ORDER BY count(item_id) DESC;

Grossed the most money? Inredible Steel Gloves (90,000)
* SELECT title, quantity * price FROM orders JOIN items ON orders.item_id = items.id GROUP BY item_id ORDER BY quantity * price DESC; 