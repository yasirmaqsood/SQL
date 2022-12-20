# SQL

## Limit & Offset
  SELECT * FROM movies Order BY Title asc Limit 5 offset 5;  // means show 5 movies starting after first 5 movies
  
## INNER JOIN
  SELECT * FROM movies Inner Join BoxOffice ON Movies.Id=Boxoffice.Movie_id Order By Rating desc;

## LEFT JOIN
  ### Find the list of all buildings that have employees 
  SELECT DISTINCT Building_name from Buildings LEFT JOIN Employees on Buildings.Building_name=Employees.Building where Employees.Building NOT NULL;
  
## IS NULL / NOT NULL
  ### Find the names of the buildings that hold no employees
  SELECT Building_name FROM Buildings LEFT JOIN Employees ON Buildings.Building_name=Employees.Building where Employees.Building IS NULL;
  
## Query with expressions
  ### List all movies and their combined sales in millions of dollars
  SELECT Distinct Title,Id,(Domestic_sales+International_sales)/1000000 AS "Total Sales" FROM Movies INNER JOIN Boxoffice on Movies.Id=Boxoffice.Movie_id Order by Id;
