# Data Analysis, Data Science, Machine Learning

- [Data Analysis, Data Science, Machine Learning](#data-analysis-data-science-machine-learning)
  - [Data Analysis](#data-analysis)
  - [Data Science](#data-science)
    - [Data Science courses](#data-science-courses)
    - [Data Science Mathematics](#data-science-mathematics)
    - [Data Science general (how to learn, advices etc.)](#data-science-general-how-to-learn-advices-etc)
  - [Machine Learning](#machine-learning)
    - [Machine learning (how to learn, advices etc.)](#machine-learning-how-to-learn-advices-etc)
    - [Machine Learning basics](#machine-learning-basics)
    - [Machine learning courses](#machine-learning-courses)
      - [Premium (Udemy, Coursera etc.)](#premium-udemy-coursera-etc)
      - [Free](#free)
    - [Artificial intelligence](#artificial-intelligence)
      - [Tutorials](#tutorials)
  - [Databases](#databases)
    - [Interactive SQL tutorials](#interactive-sql-tutorials)

## Data Analysis

- [ ] [Alex The Analyst (playlist) - Data Analyst Bootcamp](https://www.youtube.com/playlist?list=PLUaB-1hjhk8FE_XZ87vPPSfHqb6OcM0cF)

  - [x] 1. FREE Data Analyst Bootcamp!! (497K views, 6 months ago, 6:52)
  - [x] 2. How to Become a Data Analyst in 2023 (Completely FREE!) (638K views, 7 months ago, 13:59)
  - [x] 3. SQL Basics Tutorial For Beginners | Installing SQL Server Management Studio and Create Tables | 1/4 (893K views, 3 years ago, 9:37)
  - [x] 4. SQL Basics Tutorial For Beginners | Select + From Statements | 2/4 (299K views, 3 years ago, 6:14)

    > <> is the **not equal** operator.
    >
    > My comment: **SELECT** is a **projection** operation. It selects the columns that we want to see in the result.

  - [x] 5. SQL Basics Tutorial For Beginners | Where Statement | 3/4 (204K views, 3 years ago, 7:58)
  - [x] 6. SQL Basics Tutorial For Beginners | Group By + Order By Statements | 4/4 (194K views, 3 years ago, 8:09)

    > **COUNT()** is not a (regular) column (from a table). It's a **derived** column/field (and an aggregate function BTW). That's why we don't need to include it in the GROUP BY clause.
    >
    > **ORDER BY** can be used not just on one column, but on multiple columns as well. In that case, the order of columns in the ORDER BY clause matters.

  - [x] 7.  Intermediate SQL Tutorial | Inner/Outer Joins | Use Cases (315K views, 3 years ago, 15:53)

    > For inner join, it's not important which ID column we use in the SELECT clause, because they are the same. But for outer join, it's important to use the ID column from the table that we want to keep all the rows from.
    >
    > Left join keeps all the rows from the left table, and right join keeps all the rows from the right table.
    >
    > My comment (about the syntax of JOIN; BTW the word "INNER" is optional):
    >
    > ```
    > SELECT * FROM EmployeeDemographics ed
    > INNER JOIN EmployeeSalary es
    > ON ed.EmployeeID = es.EmployeeID
    > ```
    >
    > is the same as:
    >
    > ```
    > SELECT * FROM EmployeeDemographics
    > INNER JOIN EmployeeSalary
    > ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeID
    > ```
    >
    > My comment (about for example LEFT (OUTER) JOIN):
    >
    > ```
    > SELECT *
    > FROM EmployeeDemographics
    > LEFT OUTER JOIN EmployeeSalary ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeID
    > ```
    >
    > This takes everything from the "left" table (EmployeeDemographics) and matches it with the "right" table (EmployeeSalary). If there is no match, it will still take the row from the "left" table, but it will fill the columns from the "right" table with NULLs.
    >
    > My comment (about emulating FULL OUTER JOIN in MySQL)
    >
    > ```
    > SELECT *
    > FROM EmployeeDemographics
    > LEFT JOIN EmployeeSalary ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeID
    >
    > UNION
    >
    > SELECT *
    > FROM EmployeeDemographics
    > RIGHT JOIN EmployeeSalary ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeID;
    > ```

  - [x] 8. Intermediate SQL Tutorial | Unions | Union Operator (156K views, 3 years ago, 5:25)

    > Check out the previous example for FULL OUTER JOIN emulation in MySQL.
    >
    > JOIN combines both tables based on common column(s) (in our last video that column was the EmployeeID which we had in both tables), while UNION combines both tables based on common rows.
    >
    > My comments:
    >
    > - JOIN combines both tables horizontally, while UNION combines both tables vertically. In other words, JOIN puts both tables side by side, while UNION puts both tables on top of each other (below each other).
    > - Also, UNION removes the duplicates, while UNION ALL keeps the duplicates.

    > My comment (about UNION and UNION ALL):
    >
    > ```
    > SELECT *
    > FROM EmployeeDemographics
    > UNION
    > SELECT *
    > FROM EmployeeSalary;
    >
    > SELECT *
    > FROM EmployeeDemographics
    > UNION ALL
    > SELECT *
    > FROM EmployeeSalary;
    > ```
    >
    > The first query will return 5 rows, while the second query will return 6 rows (because there is one duplicate row in the EmployeeSalary table).

    > My comment (about the example in the previous video, about FULL JOIN done using UNION):
    >
    > Even though it looks as though the results is horizontal, it's actually vertical. How?
    > The first query returns 5 rows, while the second query returns 4 rows.
    > So the result of the UNION is 9 rows (4 rows are placed **below** first 5 rows and then), which is the same as the result of the FULL JOIN.

    > My comment (about selecting columns in UNION):
    >
    > ```
    > SELECT EmployeeID, FirstName, Age
    > FROM EmployeeDemographics
    > UNION
    > SELECT EmployeeID, JobTitle, Salary
    > FROM EmployeeSalary
    > ```
    >
    > If we select columns like this, we will not get the desired result. Why? Because the columns in the first query are different than the columns in the second query. So we need to select the same number of columns in both queries, and the columns need to be of the same type (or at least compatible types).

  - [x] 9. Intermediate SQL Tutorial | Case Statement | Use Cases (185K views, 3 years ago, 7:26)

    > Case statement allows us to specify a condition and then also specify what we want returned (a result) if that condition is met.
    > (Case statement allows us to create a new column based on the values of other columns.)
    >
    > We can put multiple WHEN statements in the CASE statement.
    > Example:
    >
    > ```
    > SELECT FirstName, LastName, Age,
    > CASE
    > WHEN Age < 18 THEN 'Minor'
    > WHEN Age >= 18 AND Age <= 65 THEN 'Adult'
    > ELSE 'Senior'
    > END AS 'AgeGroup'
    > FROM EmployeeDemographics;
    > ```
    >
    > Something to note is that the CASE statement is evaluated in order. So if the first WHEN statement is true, then it will return that result and not check the other WHEN statements.

    > My comment:
    >
    > So if we have multiple WHEN statements, we need to make sure that the most specific WHEN statement is first, and the most general WHEN statement is last.
    > Example:
    >
    > ```
    > SELECT FirstName, LastName, Age,
    > CASE
    > 	WHEN Age > 30 THEN 'Old'
    > 	WHEN Age = 38 THEN 'Stanley' # Previous WHEN statement is true, so this one is not checked. So this one is never true.
    > 	ELSE 'Baby'                  # Solution: change the order of WHEN statements.
    > END
    > FROM EmployeeDemographics
    > WHERE Age is NOT NULL
    > ORDER BY Age
    > ```

    > Another example (about using CASE statement with JOIN):
    >
    > ```
    > SELECT *,
    > CASE
    > 	WHEN JobTitle = 'Salesman' THEN Salary + (Salary * .10)
    > 	WHEN JobTitle = 'Accountant' THEN Salary + (Salary * .05)
    > 	WHEN JobTitle = 'HR' THEN Salary + (Salary * .000001)
    > END AS 'Salary after raise'
    > FROM EmployeeDemographics ed
    > JOIN EmployeeSalary es
    > ON ed.EmployeeID = es.EmployeeID
    > ```

  - [x] 10. Intermediate SQL Tutorial | Having Clause (102K views, 3 years ago, 3:31)

    > The HAVING clause is used to filter the results of an aggregate function.
    > Example:
    >
    > ```
    > SELECT JobTitle, COUNT(JobTitle)
    > FROM EmployeeDemographics ed
    > JOIN EmployeeSalary es
    > ON ed.EmployeeID = es.EmployeeID
    > GROUP BY JobTitle
    > HAVING COUNT(JobTitle) > 1 # This cannot be placed above GROUP BY.
    >                            # It has to be placed below GROUP BY because it's an aggregate function.
    > ```

    > The SQL query components need to be in a specific order due to the way SQL engines parse and execute queries. The SQL standard defines a particular sequence in which the clauses should appear in a SELECT statement. Here is the typical order:

    > Why does HAVING clause have to go below GROUP BY clause?
    >
    > The SQL query components need to be in a specific order due to the way SQL engines parse and execute queries. The SQL standard defines a particular sequence in which the clauses should appear in a SELECT statement. Here is the typical order:
    >
    > ```
    > 1. SELECT
    > 2. FROM
    > 3. JOIN
    > 4. WHERE
    > 5. GROUP BY
    > 6. HAVING
    > 7. ORDER BY
    > ```
    >
    > Here's why each step comes where it does:
    >
    > ```
    > 1. SELECT: Specifies the columns you want.
    > 2. FROM: Specifies the tables from which to select or delete or the tables to update.
    > 3. JOIN: Combines rows from two or more tables based on a related column between them.
    > 4. WHERE: Filters records before any groupings are made.
    > 5. GROUP BY: Groups records after the WHERE clause has been applied. The grouping is done on the basis of columns. Aggregate functions (like COUNT, AVG, MAX, etc.) then operate on these groups.
    > 6. HAVING: Filters records after the GROUP BY clause has been applied.
    > 7. ORDER BY: Sorts the records, but does this last, after all filtering and grouping have been done.
    > ```

    > My comment (a quick recap) of the difference between WHERE and HAVING:
    >
    > - WHERE filters records before any groupings are made.
    > - HAVING filters records after the GROUP BY clause has been applied.

    > My comment about aggregate functions vs. GROUP BY:
    >
    > - Aggregate functions (e.g., COUNT, SUM, AVG, MIN, MAX): Perform calculations on a set of values and return a single value.
    > - GROUP BY clause: Groups rows that have the same values in specified columns into summary rows.

  - [x] 11. Intermediate SQL Tutorial | Updating/Deleting Data (86K views, 3 years ago, 4:37)

    > The difference between INSERT and UPDATE is that INSERT adds a new row to a table, while UPDATE modifies existing rows in a table.

    > Example:
    >
    > ```
    > UPDATE EmployeeDemographics
    > SET Age = 31, Gender = 'Female'
    > WHERE EmployeeID = 1012
    > ```

    > **Good practice**, before DELETE, is to use SELECT to see what we are going to delete.
    >
    > ```
    > SELECT * FROM EmployeeDemographics
    > WHERE EmployeeID  = 1005
    > ```

    > DELETE statement is used to delete rows from a table.
    > Example:
    >
    > ```
    > DELETE FROM EmployeeDemographics
    > WHERE EmployeeID  = 1005
    > ```

  - [x] 12. Intermediate SQL Tutorial | Aliasing (85K views, 3 years ago, 6:12)

    ````
    Useful hint for writing SQL statements:
    When writing the SQL statement, first write the FROM clause with an alias. Then, when writing the SELECT statement, use the alias to refer to the table - which will give us a dropdown list of all the columns in that table.```
    ````

    > Now, continuing with the lecture...

    > Aliasing is used to give a table, or a column in a table, a temporary name.

    > My example:
    >
    > ```
    > SELECT ed.EmployeeID, ed.FirstName, ed.LastName, es.Salary
    > FROM EmployeeDemographics ed
    > JOIN EmployeeSalary es
    > ON ed.EmployeeID = es.EmployeeID
    > ```

    > Another example:
    >
    > ```
    > SELECT FirstName AS fn
    > FROM EmployeeDemographics AS ed
    > ```
    >
    > is the same as:
    >
    > ```
    > SELECT FirstName fn
    > FROM EmployeeDemographics
    > ```

    > Another example:
    >
    > ```
    > SELECT CONCAT(FirstName, ' ', LastName) AS 'Full Name'
    > FROM EmployeeDemographics
    > ```

    > Another time we'll use aliasing in the SELECT statement is when we want to use an aggregate function.
    > Example:
    >
    > ```
    > SELECT AVG(Age) AS 'Average Age'
    > FROM EmployeeDemographics
    > ```

    > Untill now, we used aliasing for **column** names. But we can also use aliasing for **table** names.
    > Example:
    >
    > ```
    > SELECT Demographics.EmployeeID
    > FROM EmployeeDemographics Demographics
    > ```

  - [x] 13. Intermediate SQL Tutorial | Partition By (163K views, 2 years ago, 4:14)

    > PARTITION BY statement is often compared to GROUP BY statement. But they are not the same. The GROUP BY statement is going to reduce the number of rows in our result set by actually "rolling them up" (by calculating the sum, or averages for each group), while the PARTITION BY statement is going to divide the result set into partitions (and change how the window function is calculated) without reducing the number of rows in our result set.

    > SELECT ed.FirstName, ed.LastName, ed.Gender, es.Salary, COUNT(Gender)
    > OVER (PARTITION BY Gender) as TotalGender
    > FROM EmployeeDemographics ed
    > JOIN EmployeeSalary es
    > ON ed.EmployeeID = es.EmployeeID

    > What is a "window function"?
    > A window function is a function that can be applied to a partition of rows. It is also called an "analytic function".
    > Another way to think about it is that a window function is a function that can be applied to a group of rows that are related to the current row.
    >
    > ChatGPT's answer:
    >
    > ```
    > A window function in SQL allows you to perform calculations across a set of table rows that are related to the current row, almost like a sliding "window" over the data. This is analogous to the way a window in a GUI application displays a subportion of the overall data. What makes window functions unique is that they provide access to more than just the current row of the query result.
    >
    > Unlike aggregate functions, which return a single result value based on a group of rows, window functions return a single value for each row from the underlying query result based on a window of rows related to that row.
    >
    > Key components of window functions:
    >
    > 1. OVER() Clause: This defines the window of rows for the function to operate on. You can specify ordering and partitioning within this clause.
    > 2. PARTITION BY: This divides the result set into partitions to which the window function is applied. For instance, if you want to operate on groups of rows having the same value in a certain column (e.g., date or category), you'd use PARTITION BY.
    > 3. ORDER BY: Within the OVER() clause, this determines the order in which rows will be processed by the window function.
    > 4. ROWS/RANGE: Specifies which rows are included in the frame. The frame is a subset of the current partition and is used for calculation in functions like running totals.
    >
    > Examples of window functions:
    >
    > - Ranking functions: ROW_NUMBER(), RANK(), DENSE_RANK(), NTILE().
    > - Analytic functions: LEAD(), LAG(), FIRST_VALUE(), LAST_VALUE().
    > - Aggregate functions: SUM(), AVG(), MIN(), MAX(). These can be used as window functions when combined with the OVER() clause.
    >
    > Using our earlier example, COUNT(Gender) OVER (PARTITION BY Gender) is a window function. For each row in the dataset, it counts the number of rows with the same Gender value.
    >
    > In essence, window functions let you perform calculations that require considering a range or "window" of rows relative to the current row, without collapsing all those rows into a single output row.
    > ```

    > Aditional explanation [Colt Steele - SQL Window Functions in 10 Minutes](https://www.youtube.com/watch?v=y1KCM8vbYe4)
    >
    > Several things to note:
    >
    > - Window functions perform aggregate operations on group of rows but they **produce a result FOR EACH ROW**. So we have individual row data alongside aggregated data.
    > - The OVER() clause constructs a window. When it's empty, the window will include all records.
    > - Use ORDER BY inside of the OVER() clause to re-order rows within each window.
    > - The PARTITION BY clause divides the window into smaller sets or partitions. The window function is applied to each partition separately and computation restarts for each partition. (Copilot suggestion)

  - [x] 14. Advanced SQL Tutorial | CTE (Common Table Expression) (214K views, 2 years ago, 3:44)

    > CTE is a common table expression and it's a named temporary result set which is used to manipulate (Copilot suggestion: the data in the result set further) the complex sub-queries data. This only exists within the scope of the statement that we're about to write. Once we cancel out of this query it's like it never existed. A CTE is also only created in memory rather than a tempdb file like a temp table would be, but in general a CTE acts very much like a subquery and so if we know how to write subqueries we can easily learn how to write CTEs.

    > CTEs are sometimes called "WITH" queries because we use the WITH keyword to create them. The syntax is as follows:
    >
    > ```
    > WITH CTE_Employee as
    > (SELECT ed.FirstName, ed.LastName, ed.Gender, es.Salary,
    > COUNT(Gender) OVER (PARTITION BY Gender) as TotalGender,
    > AVG(Salary) OVER (PARTITION BY Gender) AS AvgSalary
    > FROM EmployeeDemographics ed
    > JOIN EmployeeSalary es
    > ON ed.EmployeeID = es.EmployeeID
    > WHERE Salary > '45000')
    >
    > SELECT *
    > FROM CTE_Employee
    > ```

    > Explanation suggested by the Copilot:
    > CTE is a temporary result set that we can reference within another SQL statement. It's similar to a subquery, but it's more readable and easier to maintain.
    >
    > Example:
    >
    > ```
    > WITH EmployeeCTE AS (
    > 	SELECT *
    > 	FROM EmployeeDemographics
    > 	WHERE Age > 30
    > )
    >
    > SELECT *
    > FROM EmployeeCTE
    > ```

    > Aditional explanation (check out [LearnatKnowstar - SQL | Subquery or CTE - Which one to choose? Difference between Subquery and CTE](https://www.youtube.com/watch?v=UblBNXXojoc)):
    >
    > Excerpt:\
    > CTEs are named queries (suggested by Copilot: temporary result sets) that you can reference (multiple times if needed) within another SQL statement. They are similar to subqueries, but they are more readable and easier to maintain. They are also more flexible than subqueries. For example, you can reference a CTE multiple times in the same SELECT statement, while you can only reference a subquery once.
    > In terms of performance and in terms of how the logic is executed, they are similar to subqueries (no difference as far as I can see at the moment).

    > There are scenarios where we we can use only a CTE or only a subquery:
    >
    > - CTE can be recursive, while subquery cannot be recursive:
    >   - Recursive CTEs can reference themselves in a query. (Suggested by Copilot: This is useful for querying hierarchical data (like a tree structure) or data that has a parent-child relationship.)
    > - Corelated subqueries can reference outer table from the subquery, while CTE cannot reference outer table from the CTE.
    >
    > Suggested by Copilot: there are also scenarios where we can use both. In those cases, we should use a CTE because it's more readable and easier to maintain.

- [ ] 15. Advanced SQL Tutorial | Temp Tables (158K views, 2 years ago, 10:19)

  > Suggested by Copilot: Temp tables are like regular tables, but they are only available to the current session. They are also stored in tempdb, which is a system database. Temp tables are automatically deleted when the session that created them is closed.

  > We can hit off of this temp table multiple times which we cannot do with something like CTE or subquery, where we can only use it one time or with the subquery where we need to write it multiple times within the query. (TODO: check this)\
  > Example:
  >
  > ```
  > CREATE TEMPORARY TABLE temp_Employee (
  > EmployeeID int,
  > JobTitle varchar(100),
  > Salary int
  > )
  >
  > SELECT *
  > FROM temp_Employee
  > ```

  > Maybe the best way to work with temp tables is to take a subset of data from a (much) larger table, put it into a temp table, and then work with that temp table.\
  > Example:
  >
  > ```
  > INSERT INTO temp_Employee
  > SELECT *
  > FROM EmployeeSalary AS es
  > WHERE es.Salary > '40000'
  > ```

  > Realistic example:
  > We have a table with 100 million rows. We want to do some analysis on that table, but we don't want to do it on the entire table. So we can create a temp table with a subset of data from that table, and then do the analysis on that temp table. (Suggested by Copilot)
  >
  > ```
  > CREATE TEMPORARY TABLE temp_Employee2
  > SELECT JobTitle, Count(JobTitle), Avg(Age), Avg(Salary)
  > FROM EmployeeDemographics AS ed
  > JOIN EmployeeSalary AS es
  > ON ed.EmployeeID = es.EmployeeID
  > GROUP BY JobTitle
  > ```

  > Useful for later: A lot of times these temp tables are used in **stored procedures**.
  > (we'll need to remove the temp table before we can create it again)\
  > Example:
  >
  > ```
  > DROP TABLE IF EXISTS temp_Employee
  > CREATE TEMPORARY TABLE temp_Employee (
  > ...
  > )
  >
  > INSERT INTO temp_Employee
  > SELECT *
  > FROM ...
  >
  > SELECT *
  > FROM temp_Employee
  > ```

- [ ] 16. Advanced SQL Tutorial | String Functions + Use Cases (105K views, 2 years ago, 13:49)
- [ ] 17. Advanced SQL Tutorial | Stored Procedures + Use Cases (244K views, 2 years ago, 6:15)
- [ ] 18. Advanced SQL Tutorial | Subqueries (233K views, 2 years ago, 8:37)
- [ ] 19. Data Analyst Portfolio Project | SQL Data Exploration | Project 1/4 (1.3M views, 2 years ago, 1:17:09)
- [ ] 20. Data Analyst Portfolio Project | Data Cleaning in SQL | Project 3/4 (281K views, 2 years ago, 54:44)
- [ ] 21. Pivot Tables in Excel | Excel Tutorials for Beginners (333K views, 1 year ago, 17:35)
- [ ] 22. Formulas in Excel | Excel Tutorials for Beginners (160K views, 1 year ago, 33:54)
- [ ] 23. XLOOKUP in Excel | Excel Tutorials for Beginners (98K views, 1 year ago, 18:47)
- [ ] 24. Conditional Formatting in Excel | Excel Tutorials for Beginners (81K views, 1 year ago, 20:59)
- [ ] 25. Charts in Excel | Excel Tutorials for Beginners (60K views, 1 year ago, 15:11)
- [ ] 26. Cleaning Data in Excel | Excel Tutorials for Beginners (280K views, 1 year ago, 21:04)
- [ ] 27. Full Project in Excel | Excel Tutorials for Beginners (417K views, 1 year ago, 40:50)
- [ ] 28. How to Install Tableau and Create First Visualization | Tableau Tutorials for Beginners (402K views, 1 year ago, 17:04)
- [ ] 29. How to use Calculated Fields and Bins in Tableau | Tableau Tutorials for Beginners (118K views, 1 year ago, 6:25)
- [ ] 30. How to Create Visualizations in Tableau | Tableau Tutorials for Beginners (95K views, 1 year ago, 14:05)
- [ ] 31. How to use Joins in Tableau | Tableau Tutorials for Beginners (69K views, 1 year ago, 14:29)
- [ ] 32. Full Beginner Project in Tableau | Tableau Tutorials for Beginners (154K views, 1 year ago, 44:18)
- [ ] 33. How to Install Power BI | Building First Visualization | Microsoft Power BI for Beginners (155K views, 1 year ago, 12:50)
- [ ] 34. How to use Power Query in Power BI | Microsoft Power BI for Beginners (107K views, 1 year ago, 13:07)
- [ ] 35. How to Create and Manage Relationships in Power BI | Microsoft Power BI for Beginners (74K views, 1 year ago, 8:36)
- [ ] 36. How to use DAX in Power BI | Microsoft Power BI for Beginners (62K views, 1 year ago, 15:44)
- [ ] 37. How to use Drill Down in Power BI | Microsoft Power BI for Beginners (61K views, 1 year ago, 6:02)
- [ ] 38. How to use Conditional Formatting in Power BI | Microsoft Power BI for Beginners (49K views, 1 year ago, 9:53)
- [ ] 39. How to use Bins and Lists in Power BI | Microsoft Power BI for Beginners (32K views, 11 months ago, 9:31)
- [ ] 40. Popular Visualizations in Power BI | Microsoft Power BI for Beginners (35K views, 11 months ago, 14:14)
- [ ] 41. Full Power BI Guided Project | Microsoft Power BI for Beginners (186K views, 11 months ago, 42:37)
- [ ] 42. Installing Jupyter Notebooks/Anaconda | Python for Beginners (105K views, 10 months ago, 10:03)
- [ ] 43. Variables in Python | Python for Beginners (36K views, 10 months ago, 13:17)
- [ ] 44. Data Types in Python | Python for Beginners (33K views, 9 months ago, 21:58)
- [ ] 45. Comparison, Logical, and Membership Operators in Python | Python for Beginners (17K views, 9 months ago, 7:15)
- [ ] 46. If Else Statements in Python | Python for Beginners (16K views, 9 months ago, 6:40)
- [ ] 47. For Loops in Python | Python for Beginners (18K views, 9 months ago, 9:17)
- [ ] 48. While Loops in Python | Python for Beginners (15K views, 9 months ago, 5:40)
- [ ] 49. Functions in Python | Python for Beginners (18K views, 8 months ago, 12:44)
- [ ] 50. Converting Data Types in Python | Python for Beginners (15K views, 8 months ago, 6:36)
- [ ] 51. Building a BMI Calculator with Python | Python Projects for Beginners (29K views, 7 months ago, 14:23)
- [ ] 52. Building an Automated File Sorter in File Explorer using Python | Python Projects for Beginners (22K views, 6 months ago, 16:51)
- [ ] 53. Inspecting Web Pages with HTML | Web Scraping in Python (13K views, 2 months ago, 5:55)
- [ ] 54. BeautifulSoup + Requests | Web Scraping in Python (14K views, 2 months ago, 6:58)
- [ ] 55. Find and Find_All | Web Scraping in Python (9K views, 1 month ago, 12:10)
- [ ] 56. Scraping Data from a Real Website | Web Scraping in Python (42K views, 1 month ago, 25:23)
- [ ] 57. Reading in Files in Pandas | Python Pandas Tutorials (31K views, 6 months ago, 19:17)
- [ ] 58. Filtering Columns and Rows in Pandas | Python Pandas Tutorials (20K views, 5 months ago, 11:49)
- [ ] 59. Indexes in Pandas | Python Pandas Tutorials (13K views, 5 months ago, 11:22)
- [ ] 60. Group By and Aggregate Functions in Pandas | Python Pandas Tutorials (14K views, 4 months ago, 11:05)
- [ ] 61. Merging DataFrames in Pandas | Python Pandas Tutorials (18K views, 3 months ago, 22:09)
- [ ] 62. Creating Visualizations using Pandas Library | Python Pandas Tutorials (18K views, 3 months ago, 16:50)
- [ ] 63. Data Cleaning in Pandas | Python Pandas Tutorials (49K views, 3 months ago, 38:37)
- [ ] 64. Exploratory Data Analysis in Pandas | Python Pandas Tutorials (28K views, 2 months ago, 32:13)
- [ ] 65. Amazon Web Scraping Using Python | Data Analyst Portfolio Project (177K views, 2 years ago, 47:14)
- [ ] 66. Automating Crypto Website API Pull Using Python | Data Analyst Project (35K views, 1 year ago, 51:14)
- [ ] 67. How to Create a Portfolio Website for FREE (322K views, 2 years ago, 35:29)
- [ ] 68. Create the Perfect Data Analyst Resume | Free Templates! (78K views, 5 months ago, 17:37)
- [ ] 69. Top 3 Tips on Using LinkedIn to Land a Job (198K views, 2 years ago, 6:50)
- [ ] 70. How To Download Your Data Analyst Bootcamp Certification (Congrats!!) (25K views, 7 months ago, 1:41)

## Data Science

### Data Science courses

- [Udemy - Jose Portilla - Python for Data Science and Machine Learning Bootcamp (Rating: 4.6 out of 5 (133,378 ratings) 654,156 students, 25h, Last updated 5/2022)](https://www.udemy.com/course/python-for-data-science-and-machine-learning-bootcamp/)
- [freeCodeCamp - Santiago Basulto from RMOTR - Data Analysis with Python - Full Course for Beginners (Numpy, Pandas, Matplotlib, Seaborn)](https://www.youtube.com/watch?v=r-uOLxNrNk8)
- [freeCodeCamp (playlist) - Data Science](https://www.youtube.com/playlist?list=PLWKjhJtqVAblQe2CCWqV4Zy3LY01Z8aF1)
  > 20 videos 651,868 views Last updated on 16 Apr 2023
  - [ ] [**In progress**] Learn Data Science Tutorial - Full Course for Beginners (2.8M views, 4 years ago, ~6h)
  - [ ] Statistics - A Full University Course on Data Science Basics (2.4M views, 4 years ago, ~8.2h)
  - [ ] Python for Data Science - Course for Beginners (Learn Python, Pandas, NumPy, Matplotlib) (3.1M views, 3 years ago, ~12.2h)
  - [ ] Data Analysis with Python Course - Numpy, Pandas, Data Visualization (2M views, 2 years ago, ~10h)
  - [ ] [**In progress**] Data Analysis with Python - Full Course for Beginners (Numpy, Pandas, Matplotlib, Seaborn) (2.7M views, 3 years ago, ~4.5h)
  - [ ] Build 12 Data Science Apps with Python and Streamlit - Full Course (1.1M views, 2 years ago, ~3.2h)
  - [ ] Data Science Hands-On Crash Course (96K views, 2 years ago, ~2.5h)
  - [ ] Data Visualization with D3.js - Full Tutorial Course (1.1M views, 4 years ago, ~13h)
  - [ ] R Shiny for Data Science Tutorial – Build Interactive Data-Driven Web Apps (127K views, 1 year ago, ~1.5h)
  - [ ] R Programming Tutorial - Learn the Basics of Statistical Computing (3.6M views, 4 years ago, ~2.2h)
  - [ ] Python for Bioinformatics - Drug Discovery Using Machine Learning and Data Analysis (478K views, 2 years ago, ~2h)
  - [ ] Intro to Data Science - Crash Course for Beginners (382K views, 4 years ago, ~2h)
  - [ ] Applied Deep Learning with PyTorch - Full Course (151K views, 4 years ago, ~6h)
  - [ ] Tableau for Data Science and Data Visualization - Crash Course Tutorial (769K views, 4 years ago, ~0.5h)
  - [ ] jamovi for Data Analysis - Full Tutorial (119K views, 3 years ago, ~5h)
  - [ ] Data Analysis with Python: Part 1 of 6 (Live Course) (526K views, Streamed 2 years ago, ~1.1h)
  - [ ] [**In progress**] Data Analytics Crash Course: Teach Yourself in 30 Days (237K views, 2 years ago, ~0.9h)
  - [ ] Data Analysis with Python for Excel Users - Full Course (1.1M views, 1 year ago, ~4h)
  - [ ] Data Visualization with D3 – Full Course for Beginners [2022] (233K views, 1 year ago, ~20h)
  - [ ] Data Science Job Interview – Full Mock Interview (248K views, 4 months ago, ~1.5h)
- [Keith Galli (playlist) - Data Science](https://www.youtube.com/playlist?list=PLFCB5Dp81iNVmuoGIqcT5oF4K-7kTI5vp)
  - [ ] 1. Comprehensive Python Beautiful Soup Web Scraping Tutorial! (find/find_all, css select, scrape table) (276K views, 3 years ago, 1:13:03)
  - [ ] 2. Complete Python Pandas Data Science Tutorial! (Reading CSV/Excel files, Sorting, Filtering, Groupby) (2.8M views, 4 years ago, 1:00:27)
  - [ ] 3. Solving Real-World Data Science Interview Questions! (with Python Pandas) (75K views, 1 year ago, 1:47:50)
  - [ ] 4. 5 Jupyter Notebook Tips & Tricks to Improve your Data Science Workflow! (42K views, 1 year ago, 23:17)
  - [ ] 5. Intro to Data Visualization in Python with Matplotlib! (line graph, bar chart, title, labels, size) (215K views, 4 years ago, 32:33)
  - [ ] 6. Python Plotting Tutorial w/ Matplotlib & Pandas (Line Graph, Histogram, Pie Chart, Box & Whiskers) (285K views, 4 years ago, 1:01:30)
  - [ ] 7. Real-World Python Machine Learning Tutorial w/ Scikit Learn (sklearn basics, NLP, classifiers, etc) (220K views, 3 years ago, 1:40:49)
  - [ ] 8. Solving real world data science tasks with Python Beautiful Soup! (movie dataset creation) (270K views, 2 years ago, 3:24:18)
  - [ ] 9. Complete Python NumPy Tutorial (Creating Arrays, Indexing, Math, Statistics, Reshaping) (734K views, 4 years ago, 58:41)
  - [ ] 10. Solving real world data science tasks with Python Pandas! (1.3M views, 3 years ago, 1:26:07)
  - [ ] 11. Generating Mock Data with Python! (NumPy, Pandas, & Datetime Libraries) (25K views, 3 years ago, 1:00:26)
  - [ ] 12. Python Data Science Project Ideas! (for all skill levels) (68K views, 3 years ago, 15:45)
  - [ ] 13. Complete Natural Language Processing (NLP) Tutorial in Python! (with examples) (94K views, 1 year ago, 1:37:46)
  - [ ] 14. Complete Regular Expressions Tutorial! (with exercises for practice) (5.4K views, 4 months ago, 1:19:21)
  - [ ] 15. Introduction to Neural Networks in Python (what you need to know) | Tensorflow/Keras (81K views, 3 years ago, 1:00:37)
  - [ ] 16. Real-World Python Neural Nets Tutorial (Image Classification w/ CNN) | Tensorflow & Keras (78K views, 3 years ago, 1:01:14)
  - [ ] 17. Solving real world data science problems with Python! (computer vision edition) (36K views, 1 year ago, 1:21:38)
  - [ ] 18. How to Generate an Analytics Report (pdf) in Python! (136K views, 2 years ago, 49:15)
  - [ ] 19. How to Schedule & Automatically Run Python Code! (116K views, 2 years ago, 1:20:23)
  - [ ] 20. Solving real-world data analysis problems with Python Pandas! (Lego dataset analysis) (72K views, 1 year ago, 43:37)
  - [ ] 21. Full Data Science Mock Interview! (featuring Kylie Ying) (9.8K views, 7 months ago, 1:27:34)

### Data Science Mathematics

- [Data Nash - How Much Math Is REALLY In Data Science | What Math Do You Need For Data Science](https://www.youtube.com/watch?v=Fzfxn8U8aMw)
- [Data Nash - Every Data Scientist Should Read This Book](https://www.youtube.com/watch?v=ZbGbqUdjc28&t=86s)

### Data Science general (how to learn, advices etc.)

- [Stefanovic - FASTEST Way to Become a Data Analyst and ACTUALLY Get a Job](https://www.youtube.com/watch?v=AYWLZ1lES6g)
- [Luke Barousse - How I Would Learn to be a Data Analyst](https://www.youtube.com/watch?v=CC66RXeTn_4)
- [Power Couple - FASTEST Way to Learn Data Science and ACTUALLY Get a Job](https://www.youtube.com/watch?v=AI1eKN1Eldg)
- [Josh Brindley - FASTEST Way to become a Data Analyst and ACTUALLY get a job [2023]](https://www.youtube.com/watch?v=08DAw16x63E)
- [DataNash - How I'd Learn Data Science In 2023 (If I Could Restart) | A Beginner's Roadmap](https://www.youtube.com/watch?v=Z79AqDouS-Y)

## Machine Learning

### Machine learning (how to learn, advices etc.)

- [Dave Ebbelaar - How I'd Learn AI in 2023 (if I could start over)](https://www.youtube.com/watch?v=h2FDq3agImI)
- [How to learn AI and get RICH in the AI revolution](https://www.youtube.com/watch?v=mkRVHLQmsp4)

### Machine Learning basics

- [Programming with Mosh - Python Machine Learning Tutorial (Data Science)](https://www.youtube.com/watch?v=7eh4d6sabA0)
- [Eye On AI - Why Attention is Crucial in AI](https://www.youtube.com/shorts/Knm8iDBL1hg)
- [Weights & Biases - Scaling LLMs and Accelerating Adoption: Interview with Aidan Gomez](https://www.youtube.com/watch?v=sD24pZh7pmQ)

### Machine learning courses

#### Premium (Udemy, Coursera etc.)

- [Udemy - ZTM, Andrei Neagoie, Daniel Bourke - Complete Machine Learning & Data Science Bootcamp 2023 (Rating: 4.6 out of 5 (17,179 ratings) 99,450 students), 43.5h, Last updated 6/2023](https://www.udemy.com/course/complete-machine-learning-and-data-science-zero-to-mastery/)
- [Udemy - Jose Portilla - Python for Machine Learning & Data Science Masterclass (4.7 out of 5 (12,599 ratings) 91,232 students, 44h, Last updated 9/2021)](https://www.udemy.com/course/python-for-machine-learning-data-science-masterclass/)

#### Free

- [freeCodeCamp - Machine Learning with Python and Scikit-Learn – Full Course](https://www.youtube.com/watch?v=hDKCxebp88A)
- [freeCodeCamp (playlist) - Machine Learning](https://www.youtube.com/playlist?list=PLWKjhJtqVAblStefaz_YOVpDWqcRScc2s)
  - [ ] 1. Machine Learning for Everybody – Full Course (1.7M views, 10 months ago, 3:53:53)
  - [ ] 2. TensorFlow 2.0 Complete Course - Python Neural Networks for Beginners Tutorial (2.7M views, 3 years ago, 6:52:08)
  - [ ] 3. Self-Driving Car with JavaScript Course – Neural Networks and Machine Learning (1.9M views, 1 year ago, 2:32:40)
  - [ ] 4. No Black Box Machine Learning Course – Learn Without Libraries (280K views, 4 months ago, 3:51:31)
  - [ ] 5. PyTorch for Deep Learning & Machine Learning – Full Course (797K views, 10 months ago, 25:37:26)
  - [ ] 6. Practical Deep Learning for Coders - Full Course from fast.ai and Jeremy Howard (333K views, 2 years ago, 11:12:32)
  - [ ] 7. Deep Learning Crash Course for Beginners (580K views, 3 years ago, 1:25:39)
  - [ ] 8. Python TensorFlow for Machine Learning – Neural Network Text Classification Tutorial (218K views, 1 year ago, 1:54:11)
  - [ ] 9. Keras with TensorFlow Course - Python Deep Learning and Neural Networks for Beginners Tutorial (784K views, 3 years ago, 2:47:55)
  - [ ] 10. OpenCV Course - Full Tutorial with Python (2.5M views, 2 years ago, 3:41:42)
  - [ ] 11. How Deep Neural Networks Work - Full Course for Beginners (1.4M views, 4 years ago, 3:50:57)
  - [ ] 12. TensorFlow 2.0 Crash Course (497K views, 3 years ago, 2:13:17)
  - [ ] 13. Scikit-Learn Course - Machine Learning in Python Tutorial (399K views, 3 years ago, 2:54:25)
  - [ ] 14. Scikit-learn Crash Course - Machine Learning Library for Python (231K views, 2 years ago, 2:09:22)
  - [ ] 15. Machine Learning Course for Beginners (1.3M views, 1 year ago, 9:52:19)
  - [ ] 16. AlphaZero from Scratch – Machine Learning Tutorial (95K views, 5 months ago, 4:07:54)
  - [ ] 17. Computer Vision and Perception for Self-Driving Cars (Deep Learning Course) (225K views, 1 year ago, 1:59:38)

### Artificial intelligence

#### Tutorials

[Wes Roth - AI Tutorials](https://www.youtube.com/playlist?list=PLb1th0f6y4XQQS7qU0hIAkafMU1Kdcsi0)

- [ ] 1. Install Open Interpreter in 2 min | The free, open source CODE INTERPRETER! (24K views, 2 months ago, 8:31)
- [ ] 2. AutoGen Tutorial 🔥 How to Build POWERFUL AI Agents (90K views, 1 month ago, 30:43)
- [ ] 3. AI Plays Pokemon with Reinforcement Learning (14K views, 1 month ago, 14:25)
- [ ] 4. OpenAI Playground Assistant is POWERFUL! Here's how to BUILD one... (45K views, 12 days ago, 8:42)
- [ ] 5. Create Custom GPTs | No code AI automation | OpenAI App Store | Complete Guide (189K views, 11 days ago, 26:59)
- [ ] 6. Zapier AI Actions & GPTs | Tutorial, Examples and Automation Ideas 🔥 (50K views, 10 days ago, 30:52)
- [ ] 7. OpenAI Assistants API to Build AI Agent SWARMS. Better than AutoGen? (30K views, 6 days ago, 34:52)

## Databases

- [x] [BroCode - MySQL: JOINS are easy (INNER, LEFT, RIGHT)](https://www.youtube.com/watch?v=G3lJAxg1cy8)
- [x] [JomaClass - SQL Joins: Difference Between Inner/Left/Right/Outer Joins](https://www.youtube.com/watch?v=zGSv0VaOtR0)

- [ ] [Learn at Knowstar (playlist) - SQL Concepts](https://www.youtube.com/playlist?list=PL2-GO-f-XvjC0qhZpd0sLEcqJa6RGsaEK)
  - [ ] 1. SQL101 - DDL statements - Create, Alter, Drop (8.9K views, 4 years ago, 10:10)
  - [ ] 2. SQL DML Statements | Select | Update | Insert | Delete (8K views, 3 years ago, 19:36)
  - [ ] 3. SQL tutorial | Where Clause with Options (2K views, 3 years ago, 14:58)
  - [ ] 4. SQL Tutorial : Order By Clause (1K views, 3 years ago, 6:07)
  - [ ] 5. SQL Query | How to check for Alphanumeric values | Like | Wildcards (14K views, 2 years ago, 10:37)
  - [ ] 6. SQL Concepts | Types of Joins | SQL Tutorial (1.6K views, 2 years ago, 27:57)
  - [ ] 7. How to install SQL Server database | SQL Server Management Studio | Sample database | Free editions (2.8K views, 2 years ago, 15:28)
  - [ ] 8. SQL Query | Order of Execution (4.5K views, 1 year ago, 8:37)
  - [ ] 9. SQL | Recursive CTE | Practical Examples and 5 Use Cases | Sequences | Hierarchies (6.5K views, 1 year ago, 26:34)
  - [ ] 10. SQL Index explained in 5 minutes| What, Why & How they improve performance| Clustered |Non Clustered (5K views, 11 months ago, 5:54)
  - [ ] 11. SQL | Dynamic Data Masking | How to mask sensitive data | MS SQL (7.3K views, 10 months ago, 16:47)
  - [ ] 12. SQL | CharIndex or PatIndex | Difference #shorts (14K views, 10 months ago, 1:00)
  - [ ] 13. SQL | How to perform conditional / dynamic joins on multiple tables based on column value (5.7K views, 10 months ago, 8:52)
  - [ ] 14. SQL | Cross Apply | When to Use | Difference between Cross Apply and Inner Join (3.6K views, 8 months ago, 13:50)
  - [ ] 15. SQL | NOT IN Vs NOT EXISTS (Which one to use?) (5.9K views, 7 months ago, 10:03)
  - [ ] 16. SQL | How to add a column if it already does not exist | Error handling (3K views, 7 months ago, 5:16)
  - [ ] 17. SQL tutorial | Date Functions | Difference between DATEDIFF and DATEADD (4.5K views, 5 months ago, 19:25)
  - [ ] 18. SQL | Constraints in SQL (1.5K views, 5 months ago, 0:37)
  - [ ] 19. 8 Tips & Pointers to solve SQL Complex Queries ! (BONUS Tip Included !) (4.3K views, 5 months ago, 13:19)
  - [x] 20. SQL | Subquery or CTE - Which one to choose? Difference between Subquery and CTE (3.5K views, 4 months ago, 11:01)
  - [ ] 21. SQL CTE | Follow these 5 Rules while Creating a CTE (Avoid these mistakes !) (2K views, 4 months ago, 7:33)
  - [ ] 22. SQL Tutorial | How to Avoid a Divide By Zero Error in SQL | NULLIF (1.6K views, 4 months ago, 5:49)
  - [ ] 23. SQL | IIF Function | Learn a Shorthand for CASE #shorts (8.4K views, 3 months ago, 0:55)
  - [ ] 24. SQL Interview Question - Difference between Count(\*), Count(1), Count(colname) | Which is fastest (148K views, 2 years ago, 7:39)
  - [ ] 25. SQL Order Of Execution | In which order does the clauses in a SQL Query execute? (1.7K views, 3 months ago, 0:17)
  - [ ] 26. SQL Quiz | SQL Order By will put NULLs at top or bottom? (2.4K views, 3 months ago, 0:19)
  - [ ] 27. SQL | Windows Vs Aggregate Functions (12K views, 3 months ago, 0:37)
  - [ ] 28. SQL | How to Upload / Restore a Database in SQL Server? (6K views, 3 months ago, 0:30)
  - [ ] 29. SQL | Difference Between Union Vs Union ALL | Delete Vs Truncate | SQL Interview Questions (1.2K views, 1 month ago, 4:32)

### Interactive SQL tutorials

- [SQLBolt](https://sqlbolt.com/)
- [SQLZOO](https://sqlzoo.net/)
- [Spathon - Visual JOIN - Understand how joins work by interacting and see it visually](https://joins.spathon.com/)
