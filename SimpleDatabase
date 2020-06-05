-- Answer to the 2nd Database Assignment 2017/18
--
-- CANDIDATE NUMBER: 150074
-- Please insert your candidate number in the line above
-- Do not remove ANY lines of this template.


-- In each section below put your answer in a new line BELOW the corresponding comment.
-- Use ONE SQL statement ONLY per question.
-- If you don’t answer a question just leave the corresponding space blank. 
-- Anything that does not run in SQL you have to put in comments. Your code should never throw a syntax error.
-- Questions with syntax errors will receive zero marks.

-- DO NOT REMOVE ANY LINE FROM THIS FILE.

-- START OF ASSIGNMENT CODE


-- @@01

CREATE TABLE FW_Lorry (
vehicleRegNo CHAR(7) PRIMARY KEY,
make  ENUM('Ashok', 'Ford', 'Hyundai', 'Iveco', 'MAN', 'Mercedes-Benz', 'Scania', 'Skoda', 'Tata', 'Volvo') NOT NULL,
model VARCHAR(255),
maxLoad FLOAT(3,1) DEFAULT '40.0',
accessories SET('Combination', 'Dual', 'EOBR', 'Tandem')
);


 
-- @@02

CREATE TABLE FW_TransportRequirement (
number TINYINT UNSIGNED,
order_no INT(10) UNSIGNED NOT NULL,
lorry CHAR(7),
transport_quantity FLOAT(3,1) DEFAULT '00.0',
PRIMARY KEY (number,order_no),
CONSTRAINT FK_Order FOREIGN KEY (order_no) REFERENCES FW_SalesOrder(order_no) ON UPDATE CASCADE ON DELETE CASCADE,
CONSTRAINT FK_Lorry FOREIGN KEY (lorry) REFERENCES FW_Lorry(vehicleRegNo) ON DELETE SET NULL
);

-- @@03

ALTER TABLE FW_Person  add column dob DATE;

-- @@04

SELECT TRIM(LEADING '0' FROM house_no)
FROM FW_Person;

-- @@05

DELETE FROM FW_PhoneNumbers
WHERE phoneNum='01273007007';

-- @@06

SELECT DISTINCT salesPerson_id 
FROM FW_Places
WHERE quantity > 200;

-- @@07

SELECT DISTINCT FW_SalesPerson.person_id, FW_Person.lastName AS lastname, FW_SalesPerson.monthly_sales_target
FROM FW_SalesPerson 
INNER JOIN FW_Person ON FW_SalesPerson.person_id=FW_Person.person_id
ORDER BY lastName, monthly_sales_target DESC;

-- @@08

SELECT order_no AS number_orders
FROM FW_SalesOrder
WHERE order_date >= DATE_ADD(CURDATE(), INTERVAL -20 DAY);

-- @@09

SELECT person_id, firstName AS firstname, lastName AS lastname
FROM FW_Person
WHERE BINARY SUBSTRING(firstname,1,2) LIKE SUBSTRING(lastname,1,2); 


-- @@10

SELECT FW_Places.order_no, FW_Places.quantity * FW_SalesOrder.price AS total
FROM FW_Places, FW_SalesOrder
ORDER BY total DESC;



-- @@11

SELECT FW_Person.person_id, CONCAT(LEFT(FW_Person.firstName,1), ' ', FW_Person.lastName) AS name, FW_Places.quantity * FW_SalesOrder.price AS quarterly_sales
FROM FW_Person, FW_SalesOrder, FW_Places
WHERE QUARTER(FW_SalesOrder.order_date)=QUARTER(CURDATE());



-- @@12


SELECT salesPerson_id AS person_id, ROUND((((quantity/SUM(quantity))/COUNT(quantity) )*100), 0) AS avg_vol
FROM FW_Places 
GROUP BY salesPerson_id;

-- @@13

SELECT FW_SalesPerson.person_id AS id, (FW_Places.quantity/SUM(FW_Places.quantity)) AS avg_sales,  
(
SELECT MAX(A.quantity)  
FROM FW_Places A, FW_SalesPerson B   
WHERE FW_Places.order_no=A.order_no AND B.person_id != FW_SalesPerson.person_id
) 
AS max_cosales
FROM FW_SalesPerson, FW_Places 
GROUP BY FW_Places.order_no;

-- Do not write any DELIMITER command in the submission.
-- For Q14 and Q15 OMIT the termination symbol at the end of your function/procedure declaration


-- @@14

 


-- @@15



 




-- END OF ASSIGNMENT CODE
