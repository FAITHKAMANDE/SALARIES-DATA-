```sql
USE salaries;
SELECT * FROM salaries;

-- 1 Show all columns and rows in the table
SELECT *
FROM salaries;

-- 2 Show only the EmployeeName and Jobtitle columns
SELECT EmployeeName,Jobtitle
FROM salaries;

-- 3 Show the number of Employees in the table
SELECT COUNT(*) AS Number_of_Employees
FROM Salaries;

-- 4 Show the unique job titles in the table
SELECT DISTINCT Jobtitle
FROM salaries;

-- 5 Show the Job title  overtimepay greator than 50000 from the highest to the lowest
SELECT Jobtitle,OvertimePay
FROM salaries
WHERE OvertimePay > 50000
ORDER BY overtimePay DESC;

-- 6 Show the average Basepay for all employees into 2 decimal places.
SELECT ROUND(AVG(Basepay),2)AS avg_basepay
FROM salaries;

-- 7 Show the top 10 highest paid Employees
SELECT EmployeeName,TotalPay
FROM salaries
ORDER BY TotalPay DESC
LIMIT 10;

-- 8 Show the average of BasePay,OvertimePay and OtherPay For each Employees  from the lowest to the highest 
SELECT EmployeeName,ROUND((BasePay +OvertimePay + OtherPay)/3) AS avg_pay
FROM salaries
ORDER BY avg_pay ASC;

-- 9 Show all employees who have the word "manager" in their job title
SELECT EmployeeName,JobTitle
FROM salaries
WHERE Jobtitle LIKE "%manager%";

-- 10 Show all employees with a job title not equal to "manager"
SELECT EmployeeName,Jobtitle
FROM salaries
WHERE Jobtitle <> "manager";

-- 11 Show all employees with a total pay between 50,000 and 75,000
SELECT *
FROM salaries
WHERE TotalPay BETWEEN 50000 AND 75000;

-- 12 Show all employees with a basepay less than 50,000 or Total pay greator than 100,000
SELECT *
FROM salaries
WHERE BasePay < 50000 OR TotalPay > 100000;
  
-- 13 Show all employees with a totalpay benefits value between 125,000 and 150,000 , a job title containing "director" and the names in ascending order.
SELECT *
FROM salaries
WHERE TotalPayBenefits BETWEEN 125000 AND 150000 and Jobtitle LIKE "%Director%"
ORDER BY EmployeeName ASC;

-- 14 Show the employees and their otherpay  in descending order and in whole numbers
SELECT EmployeeName,ROUND(OtherPay)
FROM salaries
ORDER BY OtherPay DESC;

-- 15 Show all job titles with an average base pay of atleast 100,000 and order them by the average base pay in descending order
SELECT Jobtitle, AVG(Basepay) AS avgbasepay
FROM salaries
GROUP BY Jobtitle
HAVING AVG(BasePay) >= 100000
ORDER BY  avgbasepay DESC;

-- 16 Delete all the empty column
SELECT *
FROM salaries;

ALTER TABLE salaries
DROP COLUMN Notes;

ALTER TABLE salaries
DROP COLUMN Benefits;

ALTER TABLE salaries
DROP COLUMN Status;

-- 17 Update the basepay of all employees with the jobtitle "manager' by increasing it by 10%
SET sql_safe_updates = 0;
UPDATE salaries
SET Basepay = Basepay * 10/100
WHERE Jobtitle LIKE "%Manager%";

-- 18 Delete All employees who have no overtimePay
SELECT count(*)
FROM salaries
WHERE OvertimePay = 0;
DELETE FROM salaries
WHERE OvertimePay = O
```
