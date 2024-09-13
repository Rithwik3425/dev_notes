1 List the employee name, job, salary, grade and deptname for everyone in the company except clerks. Sort on salary, display the highest salary first.

```sql
SELECT e.employee_name, e.job, e.salary, e.grade, d.deptname
FROM employees e
JOIN departments d ON e.dept_id = d.dept_id
WHERE e.job != 'Clerk'
ORDER BY e.salary DESC;
```

---

2 Display all the employee details whose name consists two ‘A’s

```sql
SELECT *
FROM employees
WHERE employee_name LIKE '%A%A%';
```

---

3 Write a PL/SQL Program for Palindrome of a given number

```sql
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER;
    temp NUMBER;
    reverse_num NUMBER := 0;
BEGIN
    -- Input the number
    num := &num_input;

    -- Store the original number in a temporary variable
    temp := num;

    -- Reverse the number
    WHILE temp > 0 LOOP
        reverse_num := reverse_num * 10 + MOD(temp, 10);
        temp := TRUNC(temp / 10);
    END LOOP;

    -- Check if the original number and the reversed number are the same
    IF num = reverse_num THEN
        DBMS_OUTPUT.PUT_LINE('The number ' || num || ' is a palindrome.');
    ELSE
        DBMS_OUTPUT.PUT_LINE('The number ' || num || ' is not a palindrome.');
    END IF;
END;
/
```

---

4 Write syntax DCL commands and example to rename a column of any table..

In SQL, you can use Data Control Language (DCL) commands to control access to database objects. However, renaming a column is not typically done using DCL commands. Instead, it's usually accomplished with Data Definition Language (DDL) commands. Here's the syntax and an example using DDL commands to rename a column:

Syntax:

```sql
ALTER TABLE table_name RENAME COLUMN old_column_name TO new_column_name;
```

```sql
ALTER TABLE employees RENAME COLUMN emp_name TO employee_name;
```
___
5 Show the details of all employees hired on December 03, 98.
```sql
SELECT *
FROM employees
WHERE hire_date = TO_DATE('1998-12-03', 'YYYY-MM-DD');

```
---
6 Find the names of sailors who have reserved a red boat, and list in the order of age.
```sql
SELECT s.sailor_name
FROM Sailors s
JOIN Reserves r ON s.sid = r.sid
JOIN Boats b ON r.bid = b.bid
WHERE b.color = 'red'
ORDER BY s.age;
```
---
7 Write a PL/SQL Program for  factorial of a given number.
```sql
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER;
    factorial NUMBER := 1;
BEGIN
    -- Input the number
    num := &num_input;

    -- Calculate factorial
    IF num < 0 THEN
        DBMS_OUTPUT.PUT_LINE('Factorial is not defined for negative numbers.');
    ELSE
        FOR i IN 1..num LOOP
            factorial := factorial * i;
        END LOOP;
        DBMS_OUTPUT.PUT_LINE('Factorial of ' || num || ' is: ' || factorial);
    END IF;
END;
/
```
---
8 Give an example to represent Self join.
```sql
SELECT e.employee_name AS employee, m.employee_name AS manager
FROM employees e
JOIN employees m ON e.manager_id = m.employee_id;
```
---
9 Display employee number, name, salary prefix with the ‘$’ symbol and in descending order.
```sql
SELECT employee_number,
       employee_name,
       '$' || TO_CHAR(salary, '999999.99') AS formatted_salary
FROM employees
ORDER BY salary DESC;
```
---
10 List the no. of clerks, no. of managers department wise if both no. of clerks and no. of managers are >2.
```sql
SELECT COUNT(CASE WHEN job = 'Clerk' THEN 1 END) AS clerk_count,
       COUNT(CASE WHEN job = 'Manager' THEN 1 END) AS manager_count
FROM employees
WHERE job IN ('Clerk', 'Manager')
HAVING COUNT(CASE WHEN job = 'Clerk' THEN 1 END) > 2
   AND COUNT(CASE WHEN job = 'Manager' THEN 1 END) > 2;
```
---
11 Write a PL/SQL Program for displaying the salary of a given employee number if not give a error message using cursors.
```sql
SET SERVEROUTPUT ON;

DECLARE
    v_emp_number NUMBER := &emp_number_input;
    v_salary employees.salary%TYPE;
BEGIN
    -- Declare cursor
    CURSOR emp_cursor IS
        SELECT salary
        FROM employees
        WHERE employee_number = v_emp_number;

    -- Open cursor and fetch salary
    OPEN emp_cursor;
    FETCH emp_cursor INTO v_salary;

    -- Check if cursor found a salary
    IF emp_cursor%FOUND THEN
        DBMS_OUTPUT.PUT_LINE('Salary of employee ' || v_emp_number || ' is: $' || v_salary);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Employee with number ' || v_emp_number || ' not found.');
    END IF;

    -- Close cursor
    CLOSE emp_cursor;
EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An error occurred: ' || SQLERRM);
END;
/
```
---
12 Give necessary examples to differentiate DDL and DML.
![[Pasted image 20240424124913.png]]

---
13 Show the average salary for all departments employing more than 3 people.
```sql
SELECT d.deptname, AVG(e.salary) AS average_salary
FROM departments d
JOIN employees e ON d.dept_id = e.dept_id
GROUP BY d.deptname
HAVING COUNT(e.employee_id) > 3;
```
---
14 Display all the employee details who are completed their 30 years of service.
```sql
SELECT *
FROM employees
WHERE MONTHS_BETWEEN(SYSDATE, hire_date) / 12 >= 30;
```
---
15 Write a PL/SQL Program for reverse of a given number.
```sql
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER := &num_input;
    reversed_number NUMBER := 0;
    remainder NUMBER;
BEGIN
    -- Store the original number in a temporary variable
    remainder := num;
    
    -- Reverse the number
    WHILE remainder > 0 LOOP
        reversed_number := reversed_number * 10 + MOD(remainder, 10);
        remainder := TRUNC(remainder / 10);
    END LOOP;
    
    -- Output the reversed number
    DBMS_OUTPUT.PUT_LINE('Reverse of ' || num || ' is: ' || reversed_number);
END;
/
```
---
16 Write syntax DCL commands and example to rename a column of any table.
```sql
ALTER TABLE table_name RENAME COLUMN old_column_name TO new_column_name;
ALTER TABLE employees RENAME COLUMN emp_name TO employee_name;
```
---
17 Display all the employee details whose age is between 50 to 60 years.
```sql
SELECT *
FROM employees
WHERE TRUNC(MONTHS_BETWEEN(SYSDATE, birthdate) / 12) BETWEEN 50 AND 60;
(or)

SELECT *
FROM employees e
WHERE e.age BETWEEN 50 AND 60;
```
---
18 Write a PL/SQL Program for Implicit cursor.
```sql
SET SERVEROUTPUT ON;

DECLARE
    v_employee_id employees.employee_id%TYPE;
    v_employee_name employees.employee_name%TYPE;
    v_salary employees.salary%TYPE;
BEGIN
    -- Execute the SQL query without explicitly declaring a cursor
    SELECT employee_id, employee_name, salary
    INTO v_employee_id, v_employee_name, v_salary
    FROM employees
    WHERE department_id = 10
    AND rownum = 1; -- Selects only one record

    -- Display the fetched employee details
    DBMS_OUTPUT.PUT_LINE('Employee ID: ' || v_employee_id);
    DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_employee_name);
    DBMS_OUTPUT.PUT_LINE('Salary: ' || v_salary);
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee found for the specified criteria.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An error occurred: ' || SQLERRM);
END;
/
```
---
19 Write a PL/SQL Program for armstrong of a given number.
```sql
SET SERVEROUTPUT ON;

DECLARE
    num NUMBER := &num_input;
    temp NUMBER := num;
    digit NUMBER;
    sum NUMBER := 0;
BEGIN
    -- Calculate the number of digits in the number
    WHILE temp > 0 LOOP
        digit := MOD(temp, 10);
        sum := sum + POWER(digit, 3); -- For example, 3 is the number of digits in the number
        temp := TRUNC(temp / 10);
    END LOOP;

    -- Check if the sum of cubes of digits equals the original number
    IF sum = num THEN
        DBMS_OUTPUT.PUT_LINE(num || ' is an Armstrong number.');
    ELSE
        DBMS_OUTPUT.PUT_LINE(num || ' is not an Armstrong number.');
    END IF;
END;
/
```
---
20 Give syntax and examples for insert command (3 ways should be there).
```sql
INSERT INTO table_name
VALUES (value1, value2, ...);

INSERT INTO employees
VALUES (101, 'John', 'Doe', 'john@example.com', 50000);
---
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);

INSERT INTO employees (employee_id, first_name, last_name, email, salary)
VALUES (102, 'Jane', 'Smith', 'jane@example.com', 60000);
---
INSERT INTO table_name (column1, column2, ...)
SELECT column1, column2, ...
FROM other_table
WHERE condition;

INSERT INTO employees (employee_id, first_name, last_name, email, salary)
SELECT employee_id, first_name, last_name, email, salary
FROM temporary_employees;
```
---
21 In which year most employees were joined in the company. Display the year and no. of employees.
```sql
SELECT EXTRACT(YEAR FROM hire_date) AS join_year,
       COUNT(*) AS employee_count
FROM employees
GROUP BY EXTRACT(YEAR FROM hire_date)
ORDER BY employee_count DESC
FETCH FIRST ROW ONLY;
```
---
22 Display the average, monthly salary bill for each job type within a dept. 
```sql
SELECT d.deptname,
       e.job,
       AVG(e.salary) AS average_salary,
       COUNT(*) AS employee_count,
       AVG(e.salary) * COUNT(*) AS monthly_salary_bill
FROM employees e
JOIN departments d ON e.dept_id = d.dept_id
GROUP BY d.deptname, e.job;
```
---
23 Construct a query, which finds the job with the highest average salary.
```sql
SELECT job,
       AVG(salary) AS average_salary
FROM employees
ORDER BY AVG(salary) DESC
FETCH FIRST ROW ONLY;
```
---
24 Write a PL/SQL Program for sum of a given numbers.
```sql
SET SERVEROUTPUT ON;

DECLARE
    -- Define an array to hold the numbers
    numbers_array sys.odcinumberlist := sys.odcinumberlist(&numbers_input);
    total_sum NUMBER := 0;
BEGIN
    -- Loop through the array and calculate the sum
    FOR i IN 1..numbers_array.count LOOP
        total_sum := total_sum + numbers_array(i);
    END LOOP;

    -- Output the total sum
    DBMS_OUTPUT.PUT_LINE('Sum of the given numbers: ' || total_sum);
END;
/
```
---
25 Change the default display like this. For deptno 0 show financial department, for 20 account department, for 30 management information system, 40 electronic data processing.
```sql
SELECT 
    CASE deptno
        WHEN 0 THEN 'Financial Department'
        WHEN 20 THEN 'Account Department'
        WHEN 30 THEN 'Management Information System'
        WHEN 40 THEN 'Electronic Data Processing'
        ELSE 'Unknown Department'
    END AS department_name,
    empno,
    ename,
    job,
    mgr,
    hiredate,
    sal,
    comm
FROM
    emp;
```
---
26 Display the employee’s name, dept name, salary and hire date for deptno=20. Specify the alias ‘date-hired’ for Hire Date.
```sql
SELECT e.ename AS employee_name,
       d.dname AS department_name,
       e.sal AS salary,
       e.hiredate AS "date-hired"
FROM emp e
JOIN dept d ON e.deptno = d.deptno
WHERE e.deptno = 20;
```
---
27 Write a PL/SQL Program for displaying the salary of a given employee number if not give a error message.
```sql
SET SERVEROUTPUT ON;

DECLARE
    v_employee_id employees.employee_id%TYPE := &employee_id_input;
    v_salary employees.salary%TYPE;
BEGIN
    -- Retrieve the salary for the given employee number
    SELECT salary INTO v_salary
    FROM employees
    WHERE employee_id = v_employee_id;

    -- Display the salary if employee number exists
    DBMS_OUTPUT.PUT_LINE('Salary of Employee ' || v_employee_id || ': ' || v_salary);
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        -- Display error message if employee number is not found
        DBMS_OUTPUT.PUT_LINE('Error: Employee ' || v_employee_id || ' not found.');
    WHEN OTHERS THEN
        -- Display error message for other exceptions
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END;
/
```
---
28 List the dept details which doesn’t have any employees in it.
```sql
SELECT d.*
FROM departments d
LEFT JOIN employees e ON d.dept_id = e.dept_id
WHERE e.employee_id IS NULL;
```
---
29 Write a PL/SQL program for Explicit cursors.
```sql
SET SERVEROUTPUT ON;

DECLARE
    -- Declare variables to store employee details
    v_employee_id employees.employee_id%TYPE;
    v_employee_name employees.employee_name%TYPE;
    v_job employees.job%TYPE;
    v_salary employees.salary%TYPE;
    
    -- Declare a cursor to fetch employee details
    CURSOR emp_cursor IS
        SELECT employee_id, employee_name, job, salary
        FROM employees;
BEGIN
    -- Open the cursor and fetch employee details
    FOR emp_rec IN emp_cursor LOOP
        -- Assign fetched values to variables
        v_employee_id := emp_rec.employee_id;
        v_employee_name := emp_rec.employee_name;
        v_job := emp_rec.job;
        v_salary := emp_rec.salary;
        
        -- Display employee details
        DBMS_OUTPUT.PUT_LINE('Employee ID: ' || v_employee_id);
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_employee_name);
        DBMS_OUTPUT.PUT_LINE('Job: ' || v_job);
        DBMS_OUTPUT.PUT_LINE('Salary: ' || v_salary);
        DBMS_OUTPUT.PUT_LINE('------------------------');
    END LOOP;
END;
/
```
---
30 List the lowest paid employees working for each manager. Exclude any group where the minimum salary is less than 1000. Sort the output by salary.
```sql
SELECT manager_id,
       MIN(salary) AS lowest_salary,
       employee_id,
       ename,
       job
FROM employees
GROUP BY manager_id
HAVING MIN(salary) >= 1000
ORDER BY lowest_salary;
```
---
31 List the details of those employees whose salaries greater than any salary of their department.
							or
Find the employees who earn a salary greater than the average salary in their dept.
```sql
SELECT e.*
FROM employees e
WHERE e.salary > ANY (
    SELECT MAX(salary)
    FROM employees
    WHERE dept_id = e.dept_id
);
```
---
32 Write a PL/SQL program to display employee details whose salary is greater than average salary of all employees.
```sql
SET SERVEROUTPUT ON;

DECLARE
    v_avg_salary NUMBER;
BEGIN
    -- Calculate the average salary of all employees
    SELECT AVG(salary) INTO v_avg_salary FROM employees;
    
    -- Display employee details whose salary is greater than average
    FOR emp_rec IN (SELECT * FROM employees WHERE salary > v_avg_salary) LOOP
        DBMS_OUTPUT.PUT_LINE('Employee ID: ' || emp_rec.employee_id);
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_rec.employee_name);
        DBMS_OUTPUT.PUT_LINE('Salary: ' || emp_rec.salary);
        DBMS_OUTPUT.PUT_LINE('------------------------');
    END LOOP;
END;
/
```
---
33 Display the information of employees who earn more than their employees in deptno =30.
```sql
SELECT e.*
FROM employees e
JOIN employees e_dept30 ON e.dept_id = 30
WHERE e.salary > e_dept30.salary;
```
---
34 Display the details of employees whose manager has earning highest salary among all managers.
```sql
SELECT e.*
FROM employees e
JOIN employees m ON e.manager_id = m.employee_id
WHERE m.salary = (
    SELECT MAX(salary)
    FROM employees
    WHERE job = 'Manager'
);
```
---
35 Find the names of sailors who have reserved all boats.
```sql
SELECT s.sailor_name
FROM sailors s
WHERE NOT EXISTS (
    SELECT b.boat_id
    FROM boats b
    WHERE NOT EXISTS (
        SELECT r.reservation_id
        FROM reservations r
        WHERE r.sailor_id = s.sailor_id
        AND r.boat_id = b.boat_id
    )
);

(or)

SELECT s.sailor_name
FROM sailors s
JOIN reservations r ON s.sailor_id = r.sailor_id
GROUP BY s.sailor_id, s.sailor_name
HAVING COUNT(DISTINCT r.boat_id) = (
    SELECT COUNT(DISTINCT boat_id)
    FROM boats
);
```
---
36 Write a PL/SQL program to reverse a given string.
```sql
SET SERVEROUTPUT ON;

DECLARE
    v_input_string VARCHAR2(100) := 'your_input_string_here';
    v_output_string VARCHAR2(100);
BEGIN
    -- Reverse the input string
    FOR i IN REVERSE 1..LENGTH(v_input_string) LOOP
        v_output_string := v_output_string || SUBSTR(v_input_string, i, 1);
    END LOOP;

    -- Output the reversed string
    DBMS_OUTPUT.PUT_LINE('Original String: ' || v_input_string);
    DBMS_OUTPUT.PUT_LINE('Reversed String: ' || v_output_string);
END;
/
```
---
37 Give syntax and example each for table level integrity constraints.

Table-level integrity constraints are constraints that are defined at the table level and apply to the entire table. Here are some common types of table-level integrity constraints along with their syntax and examples:
1. **Primary Key Constraint**:
    - Syntax:
        ```sql
        CREATE TABLE table_name (
    column1 datatype PRIMARY KEY,
    column2 datatype,
    ...
);

```
    - Example:
```sql
CREATE TABLE employees (employee_id NUMBER PRIMARY KEY,employee_name VARCHAR2(100),department_id NUMBER );
```
2. **Foreign Key Constraint**:
    - Syntax:
```sql
CREATE TABLE child_table (
    column1 datatype,
    column2 datatype,
    ...
    FOREIGN KEY (column_name) REFERENCES parent_table(column_name)
);
```
Example:
```sql
		CREATE TABLE orders (
    order_id NUMBER PRIMARY KEY,
    customer_id NUMBER,
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```
3. **Unique Constraint**:
    - Syntax:
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
    UNIQUE (column_name)
);
```  
Example:
```sql
CREATE TABLE students (
    student_id NUMBER PRIMARY KEY,
    student_name VARCHAR2(100),
    email VARCHAR2(100) UNIQUE
);
```    
4. **Check Constraint**:
    - Syntax:
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
    CONSTRAINT constraint_name CHECK (condition)
);
```
Example:
```sql
CREATE TABLE products (
    product_id NUMBER PRIMARY KEY,
    product_name VARCHAR2(100),
    unit_price NUMBER,
    CONSTRAINT check_price CHECK (unit_price > 0)
);
```     
5. **Not Null Constraint**:
    - Syntax:
```sql
CREATE TABLE table_name (
    column1 datatype NOT NULL,
    column2 datatype,
    ...
);

```
Example:
```sql
CREATE TABLE departments (
    department_id NUMBER PRIMARY KEY,
    department_name VARCHAR2(100) NOT NULL
);
```
---
38 Write  any  PL/SQL  program on conditional statements.
```sql
SET SERVEROUTPUT ON;

DECLARE
    v_number NUMBER := 10; -- Change this value to test different numbers
BEGIN
    -- Check if the number is positive, negative, or zero
    IF v_number > 0 THEN
        DBMS_OUTPUT.PUT_LINE('The number ' || v_number || ' is positive.');
    ELSIF v_number < 0 THEN
        DBMS_OUTPUT.PUT_LINE('The number ' || v_number || ' is negative.');
    ELSE
        DBMS_OUTPUT.PUT_LINE('The number ' || v_number || ' is zero.');
    END IF;
END;
/
```
---
39 WRITE A PROGRAM TO PRINT EVEN NUMBERS FROM  TO 00.
```sql
SET SERVEROUTPUT ON;

DECLARE
BEGIN
    -- Loop through numbers from 1 to 100
    FOR v_number IN 1..100 LOOP
        -- Check if the number is even
        IF MOD(v_number, 2) = 0 THEN
            DBMS_OUTPUT.PUT_LINE(v_number); -- Print even number
        END IF;
    END LOOP;
END;
/
```
---
40 Give an example to represent too_many_rows exception.
```sql
DECLARE
    v_employee_name employees.employee_name%TYPE;
BEGIN
    SELECT employee_name INTO v_employee_name
    FROM employees
    WHERE employee_id = 100; -- Assume employee_id 100 exists
    
    DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_employee_name);
EXCEPTION
    WHEN TOO_MANY_ROWS THEN
        DBMS_OUTPUT.PUT_LINE('Error: Multiple employees found for the given ID.');
END;
/
```
---
41 Write a PL/SQL program that will accept an account number, amount to be debited from     ACCOUNT table. Ensure minimum balance of Rs. 500/- for any account
```sql
SET SERVEROUTPUT ON;

DECLARE
    v_account_number NUMBER := 123456789; -- Change this value to the desired account number
    v_amount_to_debit NUMBER := 200; -- Change this value to the desired amount to debit
    v_current_balance NUMBER;
BEGIN
    -- Retrieve the current balance of the account
    SELECT balance INTO v_current_balance
    FROM accounts
    WHERE account_number = v_account_number;
    
    -- Check if the current balance is sufficient for the debit amount
    IF v_current_balance - v_amount_to_debit >= 500 THEN
        -- Update the balance after debit
        UPDATE accounts
        SET balance = balance - v_amount_to_debit
        WHERE account_number = v_account_number;
        
        -- Output success message
        DBMS_OUTPUT.PUT_LINE('Debit successful. Remaining balance: Rs. ' || (v_current_balance - v_amount_to_debit));
    ELSE
        -- Output error message if minimum balance requirement is not met
        DBMS_OUTPUT.PUT_LINE('Error: Insufficient balance. Minimum balance of Rs. 500/- must be maintained.');
    END IF;
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        -- Output error message if account number is not found
        DBMS_OUTPUT.PUT_LINE('Error: Account number ' || v_account_number || ' not found.');
    WHEN OTHERS THEN
        -- Output general error message for other exceptions
        DBMS_OUTPUT.PUT_LINE('Error: An unexpected error occurred.');
END;
/
```
---
42 Give any 5 examples for Date functions.
```sql
SELECT SYSDATE FROM DUAL;

SELECT TO_CHAR(SYSDATE, 'DD-MON-YYYY') AS formatted_date FROM DUAL;

SELECT MONTHS_BETWEEN('2024-04-30', '2024-01-01') AS months_diff FROM DUAL;

SELECT ADD_MONTHS('2024-01-31', 2) AS new_date FROM DUAL;

SELECT LAST_DAY('2024-02-15') AS last_day_of_month FROM DUAL;
```
---
43 Create a referential integrity constraint between tables(on delete cascade) exist.
```sql
--Parent table
CREATE TABLE parent_table (
    parent_id NUMBER PRIMARY KEY,
    parent_name VARCHAR2(100)
);

--Create Child Table with Foreign Key Constraint and ON DELETE CASCADE:
CREATE TABLE child_table (
    child_id NUMBER PRIMARY KEY,
    parent_id NUMBER,
    child_name VARCHAR2(100),
    FOREIGN KEY (parent_id) REFERENCES parent_table(parent_id) ON DELETE CASCADE
);
```
---
44 Show the difference between commit and rollback with necessary example
1. **COMMIT:**
    - The COMMIT command is used to permanently save the changes made during the current transaction to the database.
    - Once a COMMIT command is executed, the changes become permanent and cannot be rolled back.
    - All data modifications made by the current transaction become visible to other transactions.
    - Example:
```sql
BEGIN TRANSACTION; 
UPDATE employees SET salary = salary * 1.1 WHERE department_id = 10; COMMIT;
```
2. **ROLLBACK:**
    - The ROLLBACK command is used to undo changes made during the current transaction and restore the database to its state before the transaction began.
    - It cancels the transaction, discarding any changes made during the transaction.
    - Example:
```sql
BEGIN TRANSACTION; DELETE FROM orders WHERE order_date < '2024-01-01'; ROLLBACK;
```
---
45 Give an example to represent cursor (open,fetch and close) with parameters
```sql
SET SERVEROUTPUT ON;

DECLARE
    -- Declare variables for cursor parameters
    v_department_id NUMBER := 10;
    
    -- Declare cursor with parameters
    CURSOR employee_cursor (p_department_id NUMBER) IS
        SELECT employee_name
        FROM employees
        WHERE department_id = p_department_id;
    
    -- Declare variable to store cursor result
    v_employee_name employees.employee_name%TYPE;
BEGIN
    -- Open cursor with parameter value
    OPEN employee_cursor(v_department_id);
    
    -- Fetch data from cursor
    LOOP
        FETCH employee_cursor INTO v_employee_name;
        EXIT WHEN employee_cursor%NOTFOUND;
        
        -- Process fetched data (here we print the employee names)
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_employee_name);
    END LOOP;
    
    -- Close cursor
    CLOSE employee_cursor;
END;
/
```
---
46 Give any 5 examples for character functions
```sql
SELECT UPPER('hello, world') AS uppercase_string FROM DUAL;
SELECT LOWER('Hello, World') AS lowercase_string FROM DUAL;
SELECT INITCAP('hello, world') AS initcap_string FROM DUAL;
SELECT LENGTH('Hello, World') AS string_length FROM DUAL;
SELECT SUBSTR('Hello, World', 1, 5) AS substring FROM DUAL;
```
---
47 create sequence for any table.
```sql
CREATE SEQUENCE emp_seq START WITH 1 INCREMENT BY 1;
```
---
48 List the employee details whose names have exactly five characters
```sql
SELECT *
FROM employees
WHERE LENGTH(employee_name) = 5;
```
---
49 Give an example to differentiate Truncate and delete.
```sql
TRUNCATE TABLE table_name;
DELETE FROM table_name;
```
---
50 Write a PL/SQL program to display the name, deptno, job, and salary of the top n highest-paid employees from EMP table using cursors.
```sql
DECLARE
    CURSOR top_employees IS
        SELECT employee_name, deptno, job, salary
        FROM (SELECT employee_name, deptno, job, salary, RANK() OVER (ORDER BY salary DESC) AS ranking
              FROM employees)
        WHERE ranking <= n;
BEGIN
    FOR emp_rec IN top_employees LOOP
        DBMS_OUTPUT.PUT_LINE(emp_rec.employee_name || ', ' || emp_rec.deptno || ', ' || emp_rec.job || ', ' || emp_rec.salary);
    END LOOP;
END;
/

-- Replace n with the desired number of top employees.
```
---
51 create a function in which use of  In-out parameter  existing to a  variable.
```sql
CREATE OR REPLACE FUNCTION modify_salary(
    emp_id IN NUMBER,
    INCREMENT IN NUMBER,
    new_salary OUT NUMBER
) RETURN NUMBER IS
    current_salary NUMBER;
BEGIN
    -- Get the current salary of the employee
    SELECT salary INTO current_salary FROM employees WHERE employee_id = emp_id;
    
    -- Calculate the new salary after increment
    new_salary := current_salary + INCREMENT;
    
    -- Update the salary in the database
    UPDATE employees SET salary = new_salary WHERE employee_id = emp_id;
    
    RETURN new_salary;
END;
```
---
52 Give necessary example to differentiate table and view.
* Table: A table is a physical structure that stores data in rows and columns. It holds the actual data.
```sql
CREATE TABLE employees (
    employee_id NUMBER,
    employee_name VARCHAR2(100),
    department_id NUMBER
);
```
* View: A view is a virtual table created by a query. It does not store data itself but provides a way to present data from one or more tables.
```sql
CREATE VIEW employee_details AS
SELECT employee_id, employee_name, department_name
FROM employees
JOIN departments ON employees.department_id = departments.department_id;
```
---
53 Write a PL/SQL program to represent recordtype dynamic declaration.
```sql
DECLARE
    TYPE emp_record_type IS RECORD (
        employee_id NUMBER,
        employee_name VARCHAR2(100),
        salary NUMBER
    );
    
    emp_record emp_record_type;
BEGIN
    emp_record.employee_id := 101;
    emp_record.employee_name := 'John Doe';
    emp_record.salary := 50000;
    
    DBMS_OUTPUT.PUT_LINE('Employee ID: ' || emp_record.employee_id);
    DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_record.employee_name);
    DBMS_OUTPUT.PUT_LINE('Salary: ' || emp_record.salary);
END;
/
```
---
54 Give syntax and example for column level and table level representation of foreign key.
```sql
--column-level-representation
CREATE TABLE orders (
    order_id NUMBER PRIMARY KEY,
    customer_id NUMBER,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

--table-level-representation
CREATE TABLE orders (
    order_id NUMBER PRIMARY KEY,
    customer_id NUMBER,
    CONSTRAINT fk_customer FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```
---
55 Write a PL/SQL program to represent Fibonacci series.
```sql
DECLARE
    n NUMBER := 10; -- Number of Fibonacci numbers to generate
    a NUMBER := 0;
    b NUMBER := 1;
    next_number NUMBER;
BEGIN
    FOR i IN 1..n LOOP
        DBMS_OUTPUT.PUT_LINE(a);
        next_number := a + b;
        a := b;
        b := next_number;
    END LOOP;
END;
/
```
56 Declare cursor that accepts empno and check if he is a manager then display name,job,deptno,sal of all employees working under him.
```sql
DECLARE
    v_manager_empno NUMBER := 7566; -- Example manager empno
    CURSOR emp_cursor IS
        SELECT e.employee_name, e.job, e.department_id, e.salary
        FROM employees e
        WHERE e.manager_id = v_manager_empno;
BEGIN
    FOR emp_rec IN emp_cursor LOOP
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_rec.employee_name || ', Job: ' || emp_rec.job || ', DeptNo: ' || emp_rec.department_id || ', Salary: ' || emp_rec.salary);
    END LOOP;
END;
/
```
---
57 List all analysts in department 20 whose names start with ‘M’.
```sql
SELECT *
FROM employees
WHERE job = 'ANALYST'
AND department_id = 20
AND employee_name LIKE 'M%';
```
---
58 Give an example to represent cursor (For loop) without parameters
```sql
DECLARE
    CURSOR emp_cursor IS
        SELECT employee_name, job, salary
        FROM employees;
BEGIN
    FOR emp_rec IN emp_cursor LOOP
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_rec.employee_name || ', Job: ' || emp_rec.job || ', Salary: ' || emp_rec.salary);
    END LOOP;
END;
/
```
---
59 Give an example to represent outer join.
```sql
SELECT e.employee_id, e.employee_name, d.department_name
FROM employees e
LEFT OUTER JOIN departments d ON e.department_id = d.department_id;
```
---
60 List all managers whose names end with ‘S’.
```sql
SELECT *
FROM employees
WHERE job = 'MANAGER'
AND employee_name LIKE '%S';
```
---
61 List all manager numbers without any repetition.
```sql
SELECT DISTINCT manager_id
FROM employees
WHERE job = 'MANAGER';
```
---
62 List the number of employees who are working as managers.
```sql
SELECT COUNT(*)
FROM employees
WHERE job = 'MANAGER';
```
---
63 List the number  of employees who do not avail commission in department 0
```sql
SELECT COUNT(*)
FROM employees
WHERE commission_pct IS NULL
AND department_id = 0;
```
---
64 List  all employees who are either clerks or managers in ascending order of their names
```sql
SELECT *
FROM employees
WHERE job IN ('CLERK', 'MANAGER')
ORDER BY employee_name ASC;
```
---
65 Write a PL/SQL program to display the name, deptno, job and salary of the top n highest paid employees from EMP table using cursors.
```sql
DECLARE
    n NUMBER := 5; -- Number of top employees to display
    CURSOR top_employees IS
        SELECT employee_name, department_id, job, salary
        FROM (
            SELECT employee_name, department_id, job, salary, ROW_NUMBER() OVER (ORDER BY salary DESC) AS ranking
            FROM employees
        )
        WHERE ranking <= n;
BEGIN
    FOR emp_rec IN top_employees LOOP
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_rec.employee_name || ', DeptNo: ' || emp_rec.department_id || ', Job: ' || emp_rec.job || ', Salary: ' || emp_rec.salary);
    END LOOP;
END;
/
```
---
66 List the employees belonging to the department of miller
```sql
SELECT e.*
FROM employees e
JOIN employees m ON e.department_id = m.department_id
WHERE m.employee_name = 'MILLER';
```
---
67 Write a PL/SQL program using stored procedure or function to debit an a/c and to find the balance of a particular account. Use the table BANK(ACCOUNT number(0), BNAME varchar2(5), BALANCE number(0,2)) .
```sql
CREATE OR REPLACE PROCEDURE debit_and_get_balance(
    p_account IN NUMBER,
    p_amount IN NUMBER,
    p_balance OUT NUMBER
) AS
BEGIN
    UPDATE bank
    SET balance = balance - p_amount
    WHERE account = p_account;
    
    SELECT balance INTO p_balance
    FROM bank
    WHERE account = p_account;
END;
/
```
---
68 Write a program to represent  %ISOPEN implicit cursor in an example.
```sql
DECLARE
    CURSOR emp_cursor IS
        SELECT employee_id, employee_name
        FROM employees;
BEGIN
    IF emp_cursor%ISOPEN THEN
        CLOSE emp_cursor;
    END IF;
END;
/
```
---
69 Declare a cursor that display the payslips of employees
```sql
DECLARE
    CURSOR payslip_cursor IS
        SELECT employee_id, employee_name, salary
        FROM employees;
BEGIN
    FOR payslip_rec IN payslip_cursor LOOP
        DBMS_OUTPUT.PUT_LINE('Employee ID: ' || payslip_rec.employee_id || ', Employee Name: ' || payslip_rec.employee_name || ', Salary: ' || payslip_rec.salary);
    END LOOP;
END;
/
```
---
70 List all the employees having salary equal to that of scott or ford
```sql
SELECT *
FROM employees
WHERE salary = (SELECT salary FROM employees WHERE employee_name IN ('SCOTT', 'FORD'));
```
---
71 Count the number of salesman in sales department
```sql
SELECT COUNT(*)
FROM employees
WHERE job = 'SALESMAN'
AND department_id = (SELECT department_id FROM departments WHERE department_name = 'SALES');

--(or)
SELECT COUNT(*)
FROM employees e
JOIN departments d ON e.department_id = d.department_id
WHERE e.job = 'SALESMAN'
AND d.department_name = 'SALES';
```
---
72 Write a PL/SQL program to represent %Record type dynamic declaration
```sql
DECLARE
    TYPE emp_record IS RECORD (
        employee_id employees.employee_id%TYPE,
        employee_name employees.employee_name%TYPE,
        salary employees.salary%TYPE
    );
    emp_rec emp_record;
BEGIN
    -- Dynamically initialize the record
    emp_rec.employee_id := 1001;
    emp_rec.employee_name := 'John Doe';
    emp_rec.salary := 50000;
    
    -- Print record values
    DBMS_OUTPUT.PUT_LINE('Employee ID: ' || emp_rec.employee_id);
    DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_rec.employee_name);
    DBMS_OUTPUT.PUT_LINE('Salary: ' || emp_rec.salary);
END;
/
```
---
73 Declare cursor that accepts losal and hisal and display all employees in that range
```sql
DECLARE
    CURSOR emp_cursor (p_losal NUMBER, p_hisal NUMBER) IS
        SELECT *
        FROM employees
        WHERE salary BETWEEN p_losal AND p_hisal;
BEGIN
    -- Open cursor and fetch data
    FOR emp_rec IN emp_cursor(3000, 5000) LOOP
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_rec.employee_name || ', Salary: ' || emp_rec.salary);
    END LOOP;
END;
/
```
---
74 Give syntax and example for view.
```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;

--Example
CREATE VIEW high_salary_employees AS
SELECT employee_id, employee_name, salary
FROM employees
WHERE salary > 5000;
```
---
75 Give syntax and example for sequence.
```sql
CREATE SEQUENCE sequence_name
START WITH initial_value
INCREMENT BY increment_value
MINVALUE min_value
MAXVALUE max_value
CYCLE|NOCYCLE;

--example
CREATE SEQUENCE emp_seq
START WITH 1001
INCREMENT BY 1
MINVALUE 1001
MAXVALUE 9999
NOCYCLE;
```
---
76 Write a PL/SQL program to display all employee details belonging to a particular department. The department number has to be entered through the keyboard.
```sql
DECLARE
    v_deptno NUMBER := &deptno; -- Department number entered through keyboard
BEGIN
    FOR emp_rec IN (SELECT * FROM employees WHERE department_id = v_deptno) LOOP
        DBMS_OUTPUT.PUT_LINE('Employee ID: ' || emp_rec.employee_id || ', Employee Name: ' || emp_rec.employee_name || ', Job: ' || emp_rec.job || ', Salary: ' || emp_rec.salary);
    END LOOP;
END;
/
```
---
77 Give syntax and example for user-defined data type.
```sql
CREATE TYPE type_name AS OBJECT (
    attribute1 datatype,
    attribute2 datatype,
    ...
);

--example
CREATE TYPE address_type AS OBJECT (
    street VARCHAR2(50),
    city VARCHAR2(50),
    state VARCHAR2(20),
    postal_code VARCHAR2(10)
);
```
---
78 Give an example to use a single sequence in 3 tables.
```sql
CREATE SEQUENCE emp_seq
START WITH 1001
INCREMENT BY 1
NOCYCLE;

CREATE TABLE table1 (
    id NUMBER DEFAULT emp_seq.NEXTVAL,
    column1 VARCHAR2(50),
    column2 NUMBER
);

CREATE TABLE table2 (
    id NUMBER DEFAULT emp_seq.NEXTVAL,
    column3 VARCHAR2(50),
    column4 NUMBER
);

CREATE TABLE table3 (
    id NUMBER DEFAULT emp_seq.NEXTVAL,
    column5 VARCHAR2(50),
    column6 NUMBER
);
```
---
79 Give examples to represent equi-join and non-equi join.
```sql
--Equi-join
SELECT e.employee_name, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id;

--Non-equi-join
SELECT e.employee_name, e.salary, d.department_name
FROM employees e
JOIN departments d ON e.salary BETWEEN d.min_salary AND d.max_salary;
```
---
80 List the employees who joined on 'MAY-8', '3-DEC-8', '7-DEC-8', '9-JAN-80' in ascending order of seniority.
```sql
SELECT *
FROM employees
WHERE TO_CHAR(hire_date, 'DD-MON-YY') IN ('08-MAY-08', '03-DEC-08', '07-DEC-08', '09-JAN-80')
ORDER BY hire_date;
```
---
81 Write a PL/SQL program to generate a multiplication table.
```sql
DECLARE
    v_number NUMBER := &num; -- Enter the number for which multiplication table is to be generated
BEGIN
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(v_number || ' * ' || i || ' = ' || (v_number * i));
    END LOOP;
END;
/
```
---
82 Give examples for numeric functions and single-row subqueries and multiple-row subqueries.
```sql
--Numeric Functions
SELECT ABS(-10) AS absolute_value,
       CEIL(10.5) AS ceiling_value,
       FLOOR(10.5) AS floor_value,
       ROUND(10.567, 2) AS rounded_value,
       POWER(2, 3) AS power_value,
       SQRT(16) AS square_root_value
FROM dual;

--Single-row-subquery
SELECT employee_name, salary,
       (SELECT department_name FROM departments WHERE department_id = employees.department_id) AS department_name
FROM employees;

--Multiple-row-subqurey
SELECT department_name
FROM departments
WHERE department_id IN (SELECT DISTINCT department_id FROM employees WHERE salary > 5000);
```
---
83 Write a PL/SQL function to count the number of employees present in each department. Show the three ways of executing a PL/SQL function.
```sql
--PL/SQL function
CREATE OR REPLACE FUNCTION count_employees_in_department(
    p_department_id IN NUMBER
) RETURN NUMBER IS
    v_count NUMBER;
BEGIN
    SELECT COUNT(*)
    INTO v_count
    FROM employees
    WHERE department_id = p_department_id;
    
    RETURN v_count;
END count_employees_in_department;


--Executing the function
----1. Direct call:
DECLARE
    v_emp_count NUMBER;
BEGIN
    v_emp_count := count_employees_in_department(10);
    DBMS_OUTPUT.PUT_LINE('Number of employees in department 10: ' || v_emp_count);
END;
/

----2. Stored procedure:
CREATE OR REPLACE PROCEDURE display_employee_count(
    p_department_id IN NUMBER
) AS
    v_emp_count NUMBER;
BEGIN
    v_emp_count := count_employees_in_department(p_department_id);
    DBMS_OUTPUT.PUT_LINE('Number of employees in department ' || p_department_id || ': ' || v_emp_count);
END;
/

----3. SQL query:
SELECT count_employees_in_department(20) AS emp_count
FROM dual;
```
---
84 List the employees who joined in the 80s.
```sql
SELECT *
FROM employees
WHERE EXTRACT(YEAR FROM hire_date) BETWEEN 1980 AND 1989;
```
---
85 List the employees whose Empno does not start with digit 78.
```sql
SELECT *
FROM employees
WHERE NOT REGEXP_LIKE(employee_id, '^78');
```
---
86 List the employees who joined in '98 with the job same as the most senior person of the year '98'.
```sql
SELECT *
FROM employees
WHERE EXTRACT(YEAR FROM hire_date) = 1998
AND job = (
    SELECT job
    FROM employees
    WHERE EXTRACT(YEAR FROM hire_date) = 1998
    ORDER BY hire_date
    FETCH FIRST 1 ROW ONLY
);
```
---
87 Find the total annual salary to distribute job-wise in the year 8.
```sql
SELECT job, SUM(salary) AS total_salary
FROM employees
WHERE EXTRACT(YEAR FROM hire_date) = 2008
GROUP BY job;
```
---
88 Write a PL/SQL program to represent %type dynamic declaration.
```sql
DECLARE
    v_emp_name employees.employee_name%TYPE;
BEGIN
    SELECT employee_name INTO v_emp_name FROM employees WHERE employee_id = 1001;
    DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_emp_name);
END;
/
```
---
89 Write a PL/SQL program to represent %rowtype dynamic declaration.
```sql
DECLARE
    v_emp_record employees%ROWTYPE;
BEGIN
    SELECT * INTO v_emp_record FROM employees WHERE employee_id = 1001;
    DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_emp_record.employee_name || ', Salary: ' || v_emp_record.salary);
END;
/
```
---
90 Display the Grade, Number of emps, and max salary of each grade.
```sql
SELECT grade, COUNT(*) AS num_emps, MAX(salary) AS max_salary
FROM employees
GROUP BY grade;
```
---
91 Display dname, grade, No. of emps where at least two emps are clerks.
```sql
SELECT d.department_name AS dname, e.grade, COUNT(*) AS num_emps
FROM employees e
JOIN departments d ON e.department_id = d.department_id
WHERE e.job = 'CLERK'
GROUP BY d.department_name, e.grade
HAVING COUNT(*) >= 2;
```
