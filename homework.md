# SQL Homework

The local cinema are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

## To access the database:

First, create a database called 'marvel'

```
# terminal
createdb marvel
```

Next, run the provided SQL script to populate your database:

```
# terminal
psql -d marvel -f marvel.sql
```

Use the supplied data as the source of data to answer the questions. Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1.  Return ALL the data in the 'movies' table.
SELECT * FROM movies
id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 23:10
  2 | The Incredible Hulk                 | 2008 | 15:55
  3 | Iron Man 2                          | 2010 | 14:05
  4 | Thor                                | 2011 | 12:25
  5 | Captain America: The First Avenger  | 2011 | 14:00
  6 | Avengers Assemble                   | 2012 | 12:45
  7 | Iron Man 3                          | 2013 | 12:05
  8 | Thor: The Dark World                | 2013 | 21:25
  9 | Batman Begins                       | 2005 | 17:10
 10 | Captain America: The Winter Soldier | 2014 | 19:30
 11 | Guardians of the Galaxy             | 2014 | 12:55
 12 | Avengers: Age of Ultron             | 2015 | 23:40
 13 | Ant-Man                             | 2015 | 19:45
 14 | Captain America: Civil War          | 2016 | 12:45
 15 | Doctor Strange                      | 2016 | 19:05
 16 | Guardians of the Galaxy 2           | 2017 | 21:55
 17 | Spider-Man: Homecoming              | 2017 | 14:05
 18 | Thor: Ragnarok                      | 2017 | 13:05
 19 | Black Panther                       | 2018 | 19:55
 20 | Avengers Infinity War               | 2018 | 18:50
 21 | Ant-Man and the Wasp                | 2018 | 19:55
(21 rows)


2.  Return ONLY the name column from the 'people' table
SELECT name FROM people
name         
----------------------
Gábor Budai
Abigaila Ekiert
Nuno Farinha
Ruben Franco Sanchez
Richard Haigh
Chika Kanu
Aaron McFaull
Craig Morton
John Polson
Kiran Qureshi
Ethan Radcliffe
Janapoles Ramos
Gordon Renfrew
Pauline Rudge
Martin Selis
Alex Shing
Anita Squires
Anthatony Starkes
Elisa Sveinsdottir
Hamish Whyte
Matthew Woodley
Emil Zacharczuk
(22 rows)

3.  Oops! Someone at CodeClan spelled Anthony's name wrong! Change it to reflect the proper spelling ('Anthatony Starkes' should be 'Anthony Starke').
UPDATE people set name = 'Anthony Starke' WHERE name = 'Anthatony Starkes';

Hamish Whyte
 Matthew Woodley
 Emil Zacharczuk
 Anthony Starke
(22 rows)

4.  Return ONLY your name from the 'people' table.
SELECT name FROM people WHERE name = 'Anthony Starke';

name      
----------------
Anthony Starke
(1 row)

5.  The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.
DELETE FROM movies WHERE title = 'Batman Begins';

title                
-------------------------------------
Iron Man
The Incredible Hulk
Iron Man 2
Thor
Captain America: The First Avenger
Avengers Assemble
Iron Man 3
Thor: The Dark World
Captain America: The Winter Soldier
Guardians of the Galaxy
Avengers: Age of Ultron
Ant-Man
Captain America: Civil War
Doctor Strange
Guardians of the Galaxy 2
Spider-Man: Homecoming
Thor: Ragnarok
Black Panther
Avengers Infinity War
Ant-Man and the Wasp
(20 rows)

6.  Create a new entry in the 'people' table with the name of one of the instructors.
INSERT INTO people (name) VALUES ('Katie Jeffree');
Hamish Whyte
 Matthew Woodley
 Emil Zacharczuk
 Anthony Starke
 Katie Jeffree
(23 rows)

7.  Craig Morton has decided to hijack our movie evening, remove him from the table of people.
DELETE FROM people WHERE name = 'Craig Morton';

name         
----------------------
Gábor Budai
Abigaila Ekiert
Nuno Farinha
Ruben Franco Sanchez
Richard Haigh
Chika Kanu
Aaron McFaull
John Polson
Kiran Qureshi
Ethan Radcliffe
Janapoles Ramos
Gordon Renfrew
Pauline Rudge
Martin Selis
Alex Shing
Anita Squires
Elisa Sveinsdottir
Hamish Whyte
Matthew Woodley
Emil Zacharczuk
Anthony Starke
Katie Jeffree
(22 rows)

8.  The cinema has just heard that they will be holding an exclusive midnight showing of 'Captain Marvel'!! Create a new entry in the 'movies' table to reflect this.
INSERT INTO movies (title) VALUES ('Captain Marvel');

Spider-Man: Homecoming
Thor: Ragnarok
Black Panther
Avengers Infinity War
Ant-Man and the Wasp
Captain Marvel
(21 rows)

9.  The cinema would also like to make the Guardians movies a back to back feature. Find out the show time of "Guardians of the Galaxy" and set the show time of "Guardians of the Galaxy 2" to start two hours later.

UPDATE movies set show_time = '14:55' WHERE title = 'Guardians of the Galaxy 2';

## Extension

1.  Research how to delete multiple entries from your table in a single command.

DELETE FROM people (Name)
SELECT 'Anthony Starke'
UNION ALL
SELECT 'Anita Squires'
UNION ALL
SELECT 'Janapoles Ramos'
