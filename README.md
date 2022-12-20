# SQL

## LIMIT & OFFSET
  SELECT * FROM movies Order BY Title asc Limit 5 offset 5;  // means show 5 movies starting after first 5 movies
  
## INNER JOIN
  SELECT * FROM movies Inner Join BoxOffice ON Movies.Id=Boxoffice.Movie_id Order By Rating desc;

## LEFT JOIN
  ### Find the list of all buildings that have employees 
  SELECT DISTINCT Building_name from Buildings LEFT JOIN Employees on Buildings.Building_name=Employees.Building where Employees.Building NOT NULL;
  
## IS NULL / NOT NULL
  ### Find the names of the buildings that hold no employees
  SELECT Building_name FROM Buildings LEFT JOIN Employees ON Buildings.Building_name=Employees.Building where Employees.Building IS NULL;
  
## QUERY WITH EXPRESSIONS
  ### List all movies and their combined sales in millions of dollars
  SELECT Distinct Title,Id,(Domestic_sales+International_sales)/1000000 AS "Total Sales" FROM Movies INNER JOIN Boxoffice on Movies.Id=Boxoffice.Movie_id Order by Id;
  
## AGGREGATE FUNCTIONS
  | Function     | Description |
| ---      | ---       |
| COUNT(column) | counts the number of rows in the group if no column name is specified. Otherwise, count the number of rows in the group with non-NULL values in the specified column.         |
| MIN(column)     |	Finds the smallest numerical value in the specified column for all rows in the group.|        |
| MAX(column) | Finds the largest numerical value in the specified column for all rows in the group.         |
| AVG(column)     | Finds the average numerical value in the specified column for all rows in the group.|        |
| SUM(column) |Finds the sum of all numerical values in the specified column for the rows in the group.        |
  
  #### NOTE: Group By means that all rows having common Column value (Use only those rows to perform any function)
  
  ## HAVING BY
  
    As group by is used after where clause, there needs to be any "Where Type" clause applied on grouped rows. 
    For this purpuse Having is used
  
  ## ORDER OF QUERY
    SELECT DISTINCT column, AGG_FUNC(column_or_expression), …
    FROM mytable
    JOIN another_table ON mytable.column = another_table.column
    WHERE constraint_expression
    GROUP BY column
    HAVING constraint_expression
    ORDER BY column ASC/DESC
    LIMIT count OFFSET COUNT;
    
  ### Find the total domestic and international sales that can be attributed to each director
  select Id,Director,Movie_id,Domestic_sales,International_sales, (Sum(Domestic_sales)+Sum(International_sales)) from Movies INNER JOIN Boxoffice on  
  Movies.Id=Boxoffice.Movie_id Group by director
  
  ## CREATE TABLE
  
    CREATE TABLE IF NOT EXISTS mytable (
    column DataType TableConstraint DEFAULT default_value,
    another_column DataType TableConstraint DEFAULT default_value,
    …
    );
    
   ### Example
    
    CREATE TABLE movies (
    id INTEGER PRIMARY KEY,
    title TEXT,
    director TEXT,
    year INTEGER, 
    length_minutes INTEGER
    );
    
  ## ALTER TABLE  
  
  ALTER TABLE statement to add, remove, or modify columns and table constraints.
  
  ### ADD COLUMN
  
    ALTER TABLE mytable
    ADD column DataType OptionalTableConstraint 
    DEFAULT default_value;
    
   ### REMOVE COLUMN
   
    ALTER TABLE mytable
    DROP column_to_be_deleted;
    
   ### RENAME COLUMN
   
    ALTER TABLE mytable
    RENAME TO new_table_name;
    
  ## DROP TABLE
  
    DROP TABLE table_name
  

