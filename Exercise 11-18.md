## Exercise 11 — Tasks
```sql
1.Find the number of Artists in the studio (without a HAVING clause)
  SELECT role, COUNT(*) as Number_of_artists
FROM employees
WHERE role = "Artist";

2.Find the number of Employees of each role in the studio
  SELECT role, COUNT(*)
FROM employees
GROUP BY role;

3.Find the total number of years employed by all Engineers
SELECT role, SUM(years_employed)
FROM employees
GROUP BY role
HAVING role = "Engineer";
```

## Exercise 12 — Tasks
```sql
1.Find the number of movies each director has directed
  SELECT director, COUNT(id) as Num_movies_directed
FROM movies
GROUP BY director;

2.Find the total domestic and international sales that can be attributed to each director
SELECT director, SUM(domestic_sales + international_sales) as Cumulative_sales_from_all_movies
FROM movies
    INNER JOIN boxoffice
        ON movies.id = boxoffice.movie_id
GROUP BY director;
```

## Exercise 13 — Tasks
```sql
1.Add the studio's new production, Toy Story 4 to the list of movies (you can use any director)
  INSERT INTO movies VALUES (4, "Toy Story 4", "El Directore", 2015, 90);

2.Toy Story 4 has been released to critical acclaim! It had a rating of 8.7, and made 340 million domestically and 270 million internationally. Add the record to the BoxOffice table.
  INSERT INTO boxoffice VALUES (4, 8.7, 340000000, 270000000);
  ```

  ## Exercise 14 — Tasks
  ```sql
1.The director for A Bug's Life is incorrect, it was actually directed by John Lasseter
  UPDATE movies
SET director = "John Lasseter"
WHERE id = 2;

2.The year that Toy Story 2 was released is incorrect, it was actually released in 1999
  UPDATE 
SET year = 1999
WHERE id = 3;

3.Both the title and director for Toy Story 8 is incorrect! The title should be "Toy Story 3" and it was directed by Lee Unkrich
UPDATE movies
SET title = "Toy Story 3", director = "Lee Unkrich"
WHERE id = 11;
```
## Exercise 15 — Tasks
```sql
1.This database is getting too big, lets remove all movies that were released before 2005.
  DELETE FROM movies
WHERE year < 2005;

2.Andrew Stanton has also left the studio, so please remove all movies directed by him.
  DELETE FROM movies
where director = "Andrew Stanton";
```

## Exercise 16 — Tasks
```sql
Create a new table named Database with the following columns:
– Name A string (text) describing the name of the database
– Version A number (floating point) of the latest version of this database
– Download_count An integer count of the number of times this database was downloaded

This table has no constraints.
  CREATE TABLE Database (
    Name TEXT,
    Version FLOAT,
    Download_count INTEGER
);
```

## Exercise 17 — Tasks
``` sql
1.Add a column named Aspect_ratio with a FLOAT data type to store the aspect-ratio each movie was released in.

ALTER TABLE Movies
  ADD COLUMN Aspect_ratio FLOAT DEFAULT 2.39;

2.Add another column named Language with a TEXT data type to store the language that the movie was released in. Ensure that the default for this language is English.

ALTER TABLE Movies
  ADD COLUMN Language TEXT DEFAULT "English";
  ```


## Exercise 18 — Tasks
```sql
1.We've sadly reached the end of our lessons, lets clean up by removing the Movies table

DROP TABLE Movies;

2.And drop the BoxOffice table as well

DROP TABLE BoxOffice;
```