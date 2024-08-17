# SQL Server Useful Commands

This repository contains a collection of basic and useful SQL Server commands to help you manage databases effectively.

## List all tables from a database
```sql
SELECT name 
FROM sys.tables;
```

## List all database tables with additional features
```sql
SELECT * 
FROM INFORMATION_SCHEMA.TABLES;
```

## List a specific table
```sql
SELECT * 
FROM INFORMATION_SCHEMA.TABLES 
WHERE TABLE_NAME LIKE '%NameTable%';
```

## List the configuration of a specific table
```sql
SELECT * 
FROM INFORMATION_SCHEMA.COLUMNS 
WHERE TABLE_NAME = 'NameTable';
```

## Additional Commands

### List all databases on the server
```sql
SELECT name 
FROM sys.databases;
```

### Count the number of rows in a specific table
```sql
SELECT COUNT(*) 
FROM [SchemaName].[TableName];
```

### Retrieve the top N rows from a table
```sql
SELECT TOP(N) * 
FROM [SchemaName].[TableName];
```

### Get detailed information about indexes on a table
```sql
EXEC sp_helpindex 'SchemaName.TableName';
```

### Check for null values in a column
```sql
SELECT * 
FROM [SchemaName].[TableName] 
WHERE [ColumnName] IS NULL;
```

### Update data in a table
```sql
UPDATE [SchemaName].[TableName] 
SET [ColumnName] = 'NewValue' 
WHERE [Condition];
```

### Delete data from a table
```sql
DELETE FROM [SchemaName].[TableName] 
WHERE [Condition];
```

### Create a new table
```sql
CREATE TABLE [SchemaName].[NewTableName] (
    [Column1] DataType CONSTRAINT,
    [Column2] DataType CONSTRAINT,
    ...
);
```

### Drop a table
```sql
DROP TABLE [SchemaName].[TableName];
```

### Join two tables
```sql
SELECT a.[Column1], b.[Column2] 
FROM [SchemaName].[TableA] a
JOIN [SchemaName].[TableB] b ON a.[JoinColumn] = b.[JoinColumn];
```

```markdown
# SQL Server Data Analysis Commands

This section includes SQL Server commands that are particularly useful for data analysis, allowing you to summarize, aggregate, and manipulate data effectively.

## Aggregate Functions

### Sum the values of a column
sql
SELECT SUM([ColumnName]) AS TotalSum 
FROM [SchemaName].[TableName];
```

### Calculate the average value of a column
```sql
SELECT AVG([ColumnName]) AS AverageValue 
FROM [SchemaName].[TableName];
```

### Find the minimum value in a column
```sql
SELECT MIN([ColumnName]) AS MinValue 
FROM [SchemaName].[TableName];
```

### Find the maximum value in a column
```sql
SELECT MAX([ColumnName]) AS MaxValue 
FROM [SchemaName].[TableName];
```

### Count the number of rows
```sql
SELECT COUNT(*) AS RowCount 
FROM [SchemaName].[TableName];
```

## Grouping and Filtering Data

### Group data by a specific column
```sql
SELECT [ColumnName], COUNT(*) AS CountPerGroup 
FROM [SchemaName].[TableName]
GROUP BY [ColumnName];
```

### Filter data using the WHERE clause
```sql
SELECT * 
FROM [SchemaName].[TableName] 
WHERE [ColumnName] = 'Value';
```

### Filter data with multiple conditions
```sql
SELECT * 
FROM [SchemaName].[TableName] 
WHERE [ColumnName1] = 'Value1' 
  AND [ColumnName2] = 'Value2';
```

### Filter data using the IN operator
```sql
SELECT * 
FROM [SchemaName].[TableName] 
WHERE [ColumnName] IN ('Value1', 'Value2', 'Value3');
```

## Sorting Data

### Sort data in ascending order
```sql
SELECT * 
FROM [SchemaName].[TableName] 
ORDER BY [ColumnName] ASC;
```

### Sort data in descending order
```sql
SELECT * 
FROM [SchemaName].[TableName] 
ORDER BY [ColumnName] DESC;
```

## Complex Queries

### Combine results from multiple tables (JOIN)
```sql
SELECT a.[Column1], b.[Column2] 
FROM [SchemaName].[TableA] a
INNER JOIN [SchemaName].[TableB] b ON a.[JoinColumn] = b.[JoinColumn];
```

### Calculate a new column using CASE statements
```sql
SELECT [ColumnName],
    CASE 
        WHEN [Condition1] THEN 'Result1'
        WHEN [Condition2] THEN 'Result2'
        ELSE 'Other'
    END AS NewColumnName
FROM [SchemaName].[TableName];
```

### Pivot data for better analysis
```sql
SELECT [PivotColumn], [AggregateFunction]([ValueColumn]) AS [AliasName]
FROM [SchemaName].[TableName]
GROUP BY [PivotColumn]
PIVOT ([AggregateFunction]([ValueColumn]) FOR [PivotColumn] IN ([Value1], [Value2], [Value3]));
```

### Calculate a rolling average
```sql
SELECT [ColumnName], 
       AVG([ValueColumn]) OVER (ORDER BY [DateColumn] 
                                ROWS BETWEEN 4 PRECEDING AND CURRENT ROW) AS RollingAvg
FROM [SchemaName].[TableName];
```

### Identify duplicates in data
```sql
SELECT [ColumnName], COUNT(*) AS DuplicateCount
FROM [SchemaName].[TableName]
GROUP BY [ColumnName]
HAVING COUNT(*) > 1;
```

## Subqueries and CTEs

### Use a subquery in the SELECT statement
```sql
SELECT [ColumnName],
    (SELECT MAX([OtherColumn]) 
     FROM [SchemaName].[OtherTable] 
     WHERE [Condition]) AS MaxValue
FROM [SchemaName].[TableName];
```

### Use Common Table Expressions (CTEs) for complex queries
```sql
WITH CTE AS (
    SELECT [Column1], [Column2]
    FROM [SchemaName].[TableName]
    WHERE [Condition]
)
SELECT * 
FROM CTE
WHERE [AnotherCondition];
```
