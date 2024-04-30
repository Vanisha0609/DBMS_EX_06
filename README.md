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
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/3eed9aba-1c63-46ab-bfd0-dbc7d0329511)

## QUERY:
```
SELECT c.cust_name, c.city , c.grade, s.name AS Salesman, s.city 
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;

```
## OUTPUT:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/f8cc3c19-dbe5-409a-a86a-270a9d8f3995)

## QUESTION 2:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/406a78b1-b172-4425-8e35-af1ff73c0830)

## QUERY:
```
SELECT c.cust_name,c.city ,c.grade,s.name AS Salesman,s.city
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;

```
## OUTPUT:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/0aa1c756-5d77-43c4-b8ad-a120f0a94b43)


## QUESTION 3:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/1c8efc53-b8ff-44c7-a1eb-221a9054824b)

## QUERY:
```
SELECT o.ord_no,o.purch_amt,c.cust_name,c.city
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000
ORDER BY o.ord_no;

```
## OUTPUT:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/0932ac71-8da4-40d4-b6c3-e23031f7a5c2)

## QUESTION 4:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/ae02def7-d373-4b16-a07a-b78633a73556)

## QUERY:
```
SELECT p.patient_id,p.first_name,p.last_name,p.date_of_birth,p.admission_date,p.discharge_date,p.doctor_id
FROM patients p
JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_name = 'X-Ray'AND t.result = 'Normal';

```
## OUTPUT:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/dd656231-7eb6-4a93-8118-4a31c6b4def3)

## QUESTION 5:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/95fa0cde-d683-4bbe-b4d6-d21128d06dfd)

## QUERY:
```
SELECT p.first_name AS patient_name,a.appointment_id,a.patient_id,a.doctor_id,a.appointment_date
FROM patients p
JOIN appointments a ON p.patient_id = a.patient_id;

```
## OUTPUT:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/142aaed2-1648-4b74-aee5-0aff7926b351)

## QUESTION 6:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/664b975f-77b2-4b19-b378-cac6c9f02868)

## QUERY:
```
SELECT  t.*
FROM test_results t
JOIN  patients p ON t.patient_id = p.patient_id
WHERE p.first_name = 'Alice';
```
## OUTPUT:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/fa6825e8-aa8e-442d-bf86-5174d7ea765f)

## QUESTION 7:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/57c3cff2-f31a-451f-aefe-8aa6a9efa927)

## QUERY:
```
SELECT c.cust_name, c.city, o.ord_no, o.ord_date, o.purch_amt AS "Order Amount"
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
ORDER BY o.ord_date ASC;

```
## OUTPUT:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/ef0d109a-b0ce-4947-9ae2-5e6ba3b36724)

## QUESTION 8:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/3d8198f5-c4c9-4410-b32e-934540371ced)

## QUERY:
```
SELECT c.cust_name AS "Customer Name",c.city,s.name AS "Salesman",s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12
```
## OUTPUT:
![image](https://github.com/Mena-Rossini/DBMS_EX_06/assets/102855266/17e2d7e8-8c6b-4eb9-b03e-3418950d9bf5)

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
