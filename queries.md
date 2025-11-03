![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Answers

CREATE DATABASE library;


## Iteration 2 - Joins

1. Using an **INNER JOIN**, list all books (left table) that have an assigned author (right table). The result should include only books with assigned authors.
SELECT
  b.id AS book_id,
  b.title,
  a.id AS author_id,
  a.name AS author_name,
  b.publish_date
FROM books b
INNER JOIN authors a
  ON b.author_id = a.id
ORDER BY b.id;
```sql
-- Your Query Goes Here
CREATE DATABASE library;
```

<br>

2. Using a **LEFT JOIN**, list all authors (left table) and their corresponding books on the (right table). The result should include all authors, including those who don't have any books assigned.
SELECT
  a.id AS author_id,
  a.name AS author_name,
  b.id AS book_id,
  b.title,
  b.publish_date
FROM authors a
LEFT JOIN books b
  ON b.author_id = a.id
ORDER BY a.id, b.publish_date NULLS LAST;
```sql
-- Your Query Goes Here
```

<br>

3. Using a **RIGHT JOIN**, list all books (right table) and their corresponding authors on the (left table). The result should include books without assigned authors.

SELECT
  b.id AS book_id,
  b.title,
  a.id AS author_id,
  a.name AS author_name,
  b.publish_date
FROM authors a
RIGHT JOIN books b
  ON b.author_id = a.id
ORDER BY b.id;
```sql
-- Your Query Goes Here
```

<br>

4. Using a **FULL JOIN**, list all records from the `books` and `authors` tables. The result should include all details from both tables, even if there are no match.
SELECT
  a.id   AS author_id,
  a.name AS author_name,
  b.id   AS book_id,
  b.title,
  b.publish_date
FROM authors a
FULL JOIN books b
  ON b.author_id = a.id
ORDER BY COALESCE(a.id, -1), COALESCE(b.id, -1);
```sql
-- Your Query Goes Here
```

<br>

## BONUS: Iteration 3 - Joins (continued)

1. Using an **INNER JOIN**, list all books (left table) and their corresponding publishers on the (right table). The result should include the book's title, publisher's name, and location.
SELECT
  b.title,
  p.name     AS publisher_name,
  p.location AS publisher_location,
  b.publish_date
FROM books b
INNER JOIN publishers p
  ON b.publisher_id = p.id
ORDER BY b.title;

```sql
-- Your Query Goes Here
```

<br>

2. Using a **LEFT JOIN**, list all publishers (left table) and any books they have published on the (right table). The result should include all publishers, including those who haven't published any books.

SELECT
  p.id       AS publisher_id,
  p.name     AS publisher_name,
  p.location,
  p.founded_year,
  b.id       AS book_id,
  b.title,
  b.publish_date
FROM publishers p
LEFT JOIN books b
  ON b.publisher_id = p.id
ORDER BY p.id, b.publish_date NULLS LAST;

```sql
-- Your Query Goes Here
```

<br>

3. Using a **RIGHT JOIN**, list all books (right table) and their corresponding publishers on the (left table). The result should include all books, even those without a linked publisher.

SELECT
  b.id    AS book_id,
  b.title,
  p.id    AS publisher_id,
  p.name  AS publisher_name,
  p.location,
  b.publish_date
FROM publishers p
RIGHT JOIN books b
  ON b.publisher_id = p.id
ORDER BY b.id;

```sql
-- Your Query Goes Here
```

<br>

4. Using a **FULL JOIN**, list all records from the `authors`, `books`, and `publishers` tables. The result should include all records from the three tables, even if there are no matches between them.


SELECT
  a.id   AS author_id,
  a.name AS author_name,
  b.id   AS book_id,
  b.title,
  b.publish_date,
  p.id   AS publisher_id,
  p.name AS publisher_name,
  p.location,
  p.founded_year
FROM books b
FULL JOIN authors a
  ON b.author_id = a.id
FULL JOIN publishers p
  ON b.publisher_id = p.id
ORDER BY
  COALESCE(a.id, -1),
  COALESCE(b.id, -1),
  COALESCE(p.id, -1);

```sql
-- Your Query Goes Here
```

<br>
