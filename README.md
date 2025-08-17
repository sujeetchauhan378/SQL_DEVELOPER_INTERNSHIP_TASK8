# SQL_DEVELOPER_INTERNSHIP_TASK8

📌 SQL Developer Internship – Task 8
🚀 Task: Stored Procedures and Functions
📖 Objective
Learn how to create reusable SQL blocks by working with Stored Procedures and Functions.
🛠 Tools Used

MySQL Workbench / DB Browser for SQLite

📂 Deliverables
At least one stored procedure
At least one function

🗂 Database Schema
We created a sample Employee table:
CREATE TABLE Employee (
    EmpID INT PRIMARY KEY,
    Name VARCHAR(100),
    Salary DECIMAL(10,2),
    Department VARCHAR(50)
);

INSERT INTO Employee (EmpID, Name, Salary, Department) VALUES
(1, 'Alice', 50000, 'HR'),
(2, 'Bob', 60000, 'IT'),
(3, 'Charlie', 45000, 'Finance'),
(4, 'David', 70000, 'IT');

📌 Stored Procedure Example
Increase salary of employees in a given department:
DELIMITER //

CREATE PROCEDURE IncreaseSalaryByDept(
    IN dept_name VARCHAR(50),
    IN percent_increase DECIMAL(5,2)
)
BEGIN
    UPDATE Employee
    SET Salary = Salary + (Salary * percent_increase / 100)
    WHERE Department = dept_name;
END //

DELIMITER ;

📌 Function Example
Get the yearly salary of an employee:
DELIMITER //

CREATE FUNCTION GetYearlySalary(emp_id INT)
RETURNS DECIMAL(12,2)
DETERMINISTIC
BEGIN
    DECLARE yearly_salary DECIMAL(12,2);

    SELECT Salary * 12 INTO yearly_salary
    FROM Employee
    WHERE EmpID = emp_id;

    RETURN yearly_salary;
END //

DELIMITER ;





