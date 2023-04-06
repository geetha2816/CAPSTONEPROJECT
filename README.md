# CAPSTONEPROJECT

use classicmodelss;

-- Which product line sells the most?

SELECT SUM(quantityOrdered) as total_ordered_quantity, products.productCode, products.productName,orderdetails.priceEach,products.productLine
FROM products
JOIN orderdetails
ON products. productCode = orderdetails. productCode
Group by products.productLine
order by total_ordered_quantity desc;

-- Which customer spends the most?

select sum(quantityordered*priceeach) as sales,customers.customerNumber,customers.customerName,
customers.country,orderdetails.productCode,orderdetails.quantityOrdered,orderdetails.priceEach 
from orders 
join customers on orders.customerNumber = customers.customerNumber
join orderdetails on orders.orderNumber = orderdetails.orderNumber
group by customerNumber
order by sales desc;

select sum(quantityordered*priceeach) as sales,customers.customerNumber,customers.customerName,
customers.country,orderdetails.productCode,orderdetails.quantityOrdered,orderdetails.priceEach 
from orders 
join customers using (customernumber)
join orderdetails using(orderNumber)
group by customerNumber
order by sales desc;
