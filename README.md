```markdown
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
