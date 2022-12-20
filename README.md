# SQL

## Limit & Offset
  select * from movies Order BY Title asc Limit 5 offset 5;  // means show 5 movies starting after first 5 movies
  
## INNER JOIN
  SELECT * FROM movies Inner Join BoxOffice ON Movies.Id=Boxoffice.Movie_id Order By Rating desc;
