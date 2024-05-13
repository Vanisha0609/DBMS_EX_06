# EXP No.6                                                                                 
# Date:23/04/2024
# AIM: 
To study and implement different types of joins.
# THEORY:
The SQL Joins clause is used to combine records from two or more tables in a database. A JOIN is a means for combining fields from two tables by using values common to each.The join is actually performed by the ‘where’ clause which combines specified rows of tables.
## Syntax: 
SELECT column 1, column 2, column 3... 
FROM table_name1, table_name2 
WHERE table_name1.column name = table_name2.columnname;

# Types of Joins:
Inner Join
Left (Outer) Join
Right (Outer) Join
Full (Outer) Join

## INNER JOIN
The INNER JOIN keyword selects records that have matching values in both tables.
### Syntax:
```
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```

## LEFT JOIN 
The LEFT JOIN keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.
### Syntax:
```
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;
```
## RIGHT JOIN 
The RIGHT JOIN keyword returns all records from the right table (table2), and the matching records from the left table (table1). The result is 0 records from the left side, if there is no match.
### Syntax:
```
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
```
## FULL OUTER JOIN 
The FULL OUTER JOIN keyword returns all records when there is a match in left (table1) or right (table2) table records.
FULL OUTER JOIN and FULL JOIN are the same.
### Syntax:
```
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
```
# MODULE:
## QUESTION 1:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/b2a3e6e0-6e86-4bbd-b12e-56f3f1b723bd)

## QUERY:
```
SELECT c.customer_id, c.cust_name, c.city, c.grade, c.salesman_id
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.ord_date BETWEEN '2012-08-01' AND '2012-08-30';
```
## OUTPUT:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/9c23a688-67cb-403f-91db-1cafde9d9056)

## QUESTION 2:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/a38fb2a7-3fef-43fe-b97e-53774ce286f1)

## QUERY:
```
SELECT o.ord_no, o.purch_amt, c.cust_name, c.city
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;

```
## OUTPUT:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/65edb6ad-bfcb-45a2-ae5a-e9e301ff7ac5)

## QUESTION 3:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/912b2a04-338a-462b-8a3a-6e8a72d16157)

## QUERY:
```
SELECT t.*
FROM test_results t
JOIN patients p ON t.patient_id = p.patient_id
WHERE p.first_name = 'Alice';

```
## OUTPUT:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/25a44762-a0f6-44c5-9e2c-e304c75e1596)

## QUESTION 4:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/46d32d3e-b515-48b3-837b-d8677ee21d19)

## QUERY:
```
select c.*
from CUSTOMER c
left join ORDERS o on c.customer_id=o.customer_id
where o.ord_date >'2012-08-17';

```
## OUTPUT:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/85b028ab-88e1-4ea9-8043-6d7d109c6e3a)

## QUESTION 5:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/fafe8571-6829-48ad-907c-a20c66f29eed)

## QUERY:
```
SELECT p.first_name AS patient_name
FROM patients p
JOIN doctors d ON p.doctor_id = d.doctor_id
WHERE d.first_name = 'Emily'
AND d.last_name = 'Johnson'
AND p.discharge_date IS NOT NULL;

```
## OUTPUT:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/61adacb6-9bcf-4e52-85ed-5c8d15fbaf63)

## QUESTION 6:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/7d090c39-0b2f-452f-897c-d44f1ed8db5f)

## QUERY:
```
SELECT c.cust_name AS "Customer Name",c.city AS "city",s.name AS "Salesman",s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;
```
## OUTPUT:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/1a30abaf-a9dd-429b-9377-beee1079003d)
## QUESTION 7:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/465d8365-e0c7-44e4-933a-42bfaced3af9)


## QUERY:
```
SELECT 
    p.first_name AS patient_name, 
    d.first_name AS doctor_name
FROM patients p
JOIN doctors d ON p.doctor_id = d.doctor_id
WHERE p.discharge_date IS NOT NULL;

```
## OUTPUT:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/bbef6399-8197-4c62-9165-c196bec387c5)

## QUESTION 8:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/a150015d-6ab0-4662-bc52-0d4813687dc5)

## QUERY:
```
SELECT p.first_name AS patient_name,
       t.result_id,
       t.patient_id,
       t.test_name,
       t.result,
       t.test_date
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_name='Blood Pressure';
```
## OUTPUT:
![image](https://github.com/Vanisha0609/DBMS_EX_06/assets/119104009/b8230a56-040c-4469-8bd6-8372ef164602)

## QUESTION 9:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/a1f85727-f0f9-49eb-a8e0-6930829bdc21)

## QUERY:
```
SELECT  c.*
FROM  customer c
LEFT JOIN  salesman s ON c.salesman_id = s.salesman_id
WHERE  s.name = 'Mc Lyon';

```
## OUTPUT:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/bdb255c3-46f1-44b9-ba1c-321b8fea1181)

## QUESTION 10:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/00ec9048-18c5-4023-ba80-666656e0ece3)

## QUERY:
```
SELECT c.cust_name,o.ord_no,o.ord_date,o.purch_amt
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id;

```
## OUTPUT:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/fd5a26ac-6aa2-4808-88ab-78d6350b5b95)

# RESULT:
Thus,we studied and implemented different types of joins.
