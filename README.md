# Queries SQL

--1. 
USE Magasine
SELECT p.name[Product], pr.name[Producer]
FROM Product p
RIGHT OUTER JOIN Producer pr ON p.id_producer = pr.id

--2. 
USE Magasine 
SELECT p.name[Product], d.date_of_delivery[Date], s.name[Supplier]
FROM Product p
RIGHT OUTER JOIN Delivery d ON d.id_product = d.id
RIGHT OUTER JOIN Supplier s ON d.id_supplier = s.id

--3.
 
SELECT DISTINCT c.name
FROM Category c
EXCEPT -- (вычитаем)
SELECT DISTINCT c.name
FROM  Category c
JOIN Product p ON p.id_category = c.id
JOIN Producer pr ON p.id_producer = pr.id 
WHERE pr.name = 'Грант'

--4. 

SELECT pr.name
FROM Producer pr
EXCEPT -- (вычитаем)
SELECT DISTINCT pr.name
FROM Product p
JOIN Producer pr ON p.id_producer = pr.id
JOIN Category c ON p.id_category = c.id
WHERE c.name = 'Алкоголь'
