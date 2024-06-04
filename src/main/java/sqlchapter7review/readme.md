<h1>Querying Multiple Tables:</h1>

<h2>In this chapter Ashya will learn how to use SQL to join two or more tables together,including INNER and OUTER (LEFT,RIGHT,and FULL) joins,and advanced joins(cross,natural,and self joins). She will learn about set theory annd how to combine queries using UNION and UNION ALL, and how to get the differences and intersections of different queries.Lastly, Ashya will learn how to optimize queries when they contain multiple tables.</h2>
<h3>What are Joins?</h3>
<h3>Joins in SQL are basically used to fetch the rows from two or more related tables.The tables involved in the join are related through using the primary key and foreign key relationship but it is not mandatory!The tables involved must have a common field.Common filed means both the column must be compatible in terms of data <type based on that common field the Joins retrieved the data.</h3>
<p>INNER JOIN: The inner join returns only the matching records from both the tables involved in the join.Non-matching records are eliminated.</p>
An INNER JOIN in MySQL is created by using the INNER JOIN keyword. An INNER JOIN is the most common type of join used in real-time applications. The Inner Join in MySQL is used to return only the matching rows from both the tables involved in the join by removing the non-matching records. The following diagram is the pictorial representation of Inner Join.

- The INNER JOIN returns the rows in the result set where the column value in a row of table1 is equal to the column value in a row of table2.
In INNER JOIN the ON clause defines the columns and condition to be evaluated.

- you can use either the INNER JOIN or JOIN keyword to perform Inner Join. If you use only the JOIN keyword, then it is also going to perform Inner JOIN in MySQL.
<h2> Outer Join in MySQL</h2>
  Unlike INNER JOIN, the OUTER JOIN returns matched data rows as well as unmatched data rows from both the tables involved in the join. Outer join is again classified into three types.

1. Left outer join
2. Right outer join
3. Full outer join

The LEFT OUTER JOIN in MySQL retrieves all the matching rows from both the tables as well as non-matching rows from the left side table. In this case, the un-matching data will take a null value. The most obvious question is which is the left table and which is the right table? The answer is, the table mentioned to the left of the LEFT OUTER JOIN keyword is the left table, and the table mentioned to the right of the LEFT OUTER JOIN keyword is the right table. The following diagram shows the pictorial representation of Left Outer Join in MySQL.

Now using LEFT OUTER JOIN, we can join the 2 tables and display the information of employees and the projects they are working on, we also get the details of employees who are not working on any project. The Following is the Left Outer Join Query which is joining the Employee and Projects tables and will give the results shown in the above image.

SELECT Id as EmployeeID, Name, Department, City, Title as Project, ClientId
FROM Employee
LEFT OUTER JOIN Projects
ON Employee.Id = Projects.EmployeeId;

If we look at the output, here, we got all 10 rows (i.e. all the rows from the Employee Table) including the row that has a null value for the EmployeeId column in the Projects table. So, this proofs that the Left Outer Join will retrieve all the rows from the Left-hand side Table including the rows that have a null foreign key value in the right-hand side table.

Instead of using the LEFT OUTER JOIN keyword, you can also use the LEFT JOIN keyword as shown in the below SQL Query, and also you will get the same output as the previous one.

Right Outer Join in MySQL
The RIGHT OUTER JOIN in MySQL retrieves all the matching rows from both the tables as well as non-matching rows from the right-side table. In this case, the un-matching data will take a null value. The most obvious question is which is the left table and which is the right table? The answer is, the table mentioned to the left of the RIGHT OUTER JOIN keyword is the left table, and the table mentioned to the right of the RIGHT OUTER JOIN keyword is the right table.
ow using RIGHT OUTER JOIN, we can join the 2 tables and display the information of employees and the projects they are working on, we also get the details of projects which are not yet assigned to any employee. The Following is the Right Outer Join Query which is joining the Employee and Projects tables and will give the results shown in the above image.

SELECT Employee.Id as EmployeeId, Name, Department, City, Title as Project
FROM Employee
RIGHT OUTER JOIN Projects
ON Employee.Id = Projects.EmployeeId;
Full Outer Join in MySQL

The FULL OUTER JOIN retrieves all the matching rows from both the tables as well as non-matching rows from both the tables involved in the Join. In this case, the un-matching data will take a null value. MySQL doesn’t support FULL OUTER JOIN; we will achieve the FULL OUTER JOIN using UNION Operator in MySQL. The syntax to achieve Full Outer Join in MySQL using the UNION operator is given below.

Now execute the following SQL statement. You will get all the data rows from the left as well as from the right table. The data rows from the left and right table column where the values don’t match will contain NULL means no value.

SELECT Employee.Id as EmployeeId, Name, Department, City, Title as Project
FROM Employee
LEFT OUTER JOIN Projects
ON Employee.Id = Projects.EmployeeId
UNION
SELECT Employee.Id as EmployeeId, Name, Department, City, Title as Project
FROM Employee
RIGHT OUTER JOIN Projects
ON Employee.Id = Projects.EmployeeId;

Note: If you want to select all the records from both the right and left-side table then you need to use the Full Outer Join. Or in other words, if you want to retrieve all the matching rows as well as all non-matching rows from both the tables then you need to use Full Outer Join in MySQL. Further, there is no Full Outer Join Keyword, instead, using the UNION operator we can achieve Full Outer Join.

Cross Join in MySQL
The CROSS JOIN is created by using the CROSS JOIN keyword. The CROSS JOIN does not contain an ON clause. Unlike INNER JOIN, the CROSS-JOIN returns matched data rows as well as unmatched data rows from the table. When we combine two or more tables with each other without any condition (where or on) then we call such type of joins as cross join. In Cross Join, each record of a table is joined with each record of the other table involved in the join.

A Cross Join in MySQL produces the Cartesian product of the tables involved in the join. The Cartesian product means the number of records present in the first table is multiplied by the number of records present in the second table. Please have a look at the below SQL query which is an example of Cross Join for joining the Employee and Projects Table.

SELECT Employee.Id as EmployeeId, Name, Department, City, Title as Project
FROM Employee
CROSS JOIN Projects;
The Employee is the LEFT Table which contains 10 rows and Projects is the RIGHT Table which contains 11 rows. So, when you execute the above query, you will get 110 records in the result set. 
