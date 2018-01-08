# Data Wrangling Notes

## 9.4 SQL Data Types

Here's just a sampling of the many data types that SQL supports. We won't be using most of these types in this course, though.

The exact list of types differs from one database to another. For a full list of types, check the manual for your database, such as this one for PostgreSQL.

http://www.postgresql.org/docs/9.4/static/datatype.html

### Text and string types
**text** — a string of any length, like Python str or unicode types.

**char(n)** — a string of exactly n characters.

**varchar(n)** — a string of up to n characters.

### Numeric types
**integer** — an integer value, like Python int.

**real** — a floating-point value, like Python float. Accurate up to six decimal places.

**double precision** — a higher-precision floating-point value. Accurate up to 15 decimal places.

**decimal** — an exact decimal value.

### Date and time types
**date** — a calendar date; including year, month, and day.

**time** — a time of day.

**timestamp** — a date and time together.

## 9.5 3 Different Query Options

```
SELECT name FROM animals WHERE (NOT species = 'gorilla') and (NOT name != 'Max');

SELECT name FROM animals WHERE NOT (species = 'gorilla' OR name = 'Max');

SELECT name FROM animals WHERE species != 'gorilla' and name != 'Max';
```

## 9.6
#### Can use all same operators as Python

=, !=, >, >=, <, <=

#### Cannot do this:

'1995-01-01' <= birthdate <= '1998-12-31'

#### Must do this instead:

birthdate >= '1995-01-01' and birthdate <= '1998-12-31'

## 9.7 Database reference

### Reference
For reference, here's a list of all the tables in the zoo database:

#### animals
This table lists individual animals in the zoo. Each animal has only one row. There may be multiple animals with the same name, or even multiple animals with the same name and species.

- name — the animal's name (example: 'George')
- species — the animal's species (example: 'gorilla')
- birthdate — the animal's date of birth (example: '1998-05-18')

#### diet
This table matches up species with the foods they eat. Every species in the zoo eats at least one sort of food, and many eat more than one. If a species eats more than one food, there will be more than one row for that species.

- species — the name of a species (example: 'hyena')
- food — the name of a food that species eats (example: 'meat')

#### taxonomy
This table gives the (partial) biological taxonomic names for each species in the zoo. It can be used to find which species are more closely related to each other evolutionarily.

- name — the common name of the species (e.g. 'jackal')
- species — the taxonomic species name (e.g. 'aureus')
- genus — the taxonomic genus name (e.g. 'Canis')
- family — the taxonomic family name (e.g. 'Canidae')
- t_order — the taxonomic order name (e.g. 'Carnivora')

If you've never heard of this classification, don't worry about it; the details won't be necessary for this course. But if you're curious, Wikipedia articles Taxonomy and Biological classification may help.

#### ordernames
This table gives the common names for each of the taxonomic orders in the taxonomy table.

- t_order — the taxonomic order name (e.g. 'Cetacea')
- name — the common name (e.g. 'whales and dolphins')

### The SQL for it
And here are the SQL commands that were used to create those tables. We won't cover the **create table** command until lesson 4, but it may be interesting to look at:

```
create table animals (  
      name text,
      species text,
      birthdate date);

create table diet (
      species text,
      food text);  

create table taxonomy (
      name text,
      species text,
      genus text,
      family text,
      t_order text); 

create table ordernames (
      t_order text,
      name text);
```


*Remember: In SQL, we always put string and date values inside single quotes.*

## 9.9 Select clauses

### where
The where clause expresses restrictions — filtering a table for rows that follow a particular rule. where supports equalities, inequalities, and boolean operators (among other things):

- where species = 'gorilla' — return only rows that have 'gorilla' as the value of the species column.
- where name >= 'George' — return only rows where the name column is alphabetically after 'George'.
- where species != 'gorilla' and name != 'George' — return only rows where species isn't 'gorilla' and name isn't 'George'.

### limit / offset
The limit clause sets a limit on how many rows to return in the result table. The optional offset clause says how far to skip ahead into the results. So limit 10 offset 100 will return 10 results starting with the 101st.

### order by
The order by clause tells the database how to sort the results — usually according to one or more columns. So order by species, name says to sort results first by the species column, then by name within each species. Ordering happens before limit/offset, so you can use them together to extract pages of alphabetized results. (Think of the pages of a dictionary.) The optional desc modifier tells the database to order results in descending order — for instance from large numbers to small ones, or from Z to A.

### group by
The group by clause is only used with aggregations, such as max or sum. Without a group by clause, a select statement with an aggregation will aggregate over the whole selected table(s), returning only one row. With a group by clause, it will return one row for each distinct value of the column or expression in the group by clause.

### Table used in this quiz

#### animals
This table lists individual animals in the zoo. Each animal has only one row. There may be multiple animals with the same name, or even multiple animals with the same name and species.

- name — the animal's name (example: 'George')
- species — the animal's species (example: 'gorilla')
- birthdate — the animal's date of birth (example: '1998-05-18')

## 9.13 Joining tables

```QUERY = '''
SELECT name
from animals, diet
where animals.species = diet.species and food = 'fish'
'''

Alternate format
QUERY = '''
SELECT name
from animals join diet
on animals.species = diet.species
where food = 'fish'
'''
```

## 11.3 Normalized Design

### Rules for normalized tables:

#### 1. Every row has the same number of columns.
In practice, the database system won't let us literally have different numbers of columns in different rows. But if we have columns that are sometimes empty (null) and sometimes not, or if we stuff multiple values into a single field, we're bending this rule.

The example to keep in mind here is the diet table from the zoo database. Instead of trying to stuff multiple foods for a species into a single row about that species, we separate them out. This makes it much easier to do aggregations and comparisons.

#### 2. There is a unique key and everything in a row says something about the key.
The key may be one column or more than one. It may even be the whole row, as in the diet table. But we don't have duplicate rows in a table.

More importantly, if we are storing non-unique facts — such as people's names — we distinguish them using a unique identifier such as a serial number. This makes sure that we don't combine two people's grades or parking tickets just because they have the same name.

#### 3. Facts that don't relate to the key belong in different tables.
The example here was the items table, which had items, their locations, and the location's street addresses in it. The address isn't a fact about the item; it's a fact about the location. Moving it to a separate table saves space and reduces ambiguity, and we can always reconstitute the original table using a join.

#### 4. Tables shouldn't imply relationships that don't exist.
The example here was the job_skills table, where a single row listed one of a person's technology skills (like 'Linux') and one of their language skills (like 'French'). This made it look like their Linux knowledge was specific to French, or vice versa ... when that isn't the case in the real world. Normalizing this involved splitting the tech skills and job skills into separate tables.

### Additional Reading:

http://www.bkent.net/Doc/simple5.htm

https://en.wikipedia.org/wiki/Database_normalization

## SQL Tutorial
http://www.dofactory.com/sql/tutorial

## 11.11 Join types

### Counting what isn’t there
Counting rows in a single table is something you’ve seen many times before in this course. A column aggregated with the **count** aggregation function will return the number of rows in the table, or the number of rows for each value of a **group by** clause.

For instance, you saw queries like these back in Lesson 2:

```
select count(*) from animals;
```
*-- returns the number of animals in the zoo*

```
select count(*) from animals where species = ‘gorilla’;
```
*-- returns the number of gorillas*

```
select species, count(*) from animals group by species;
```
*-- returns each species’ name and the number of animals of that species*

Things get a little more complicated if you want to count the results of a join. Consider these tables we saw earlier in this lesson, the products and sales tables for a store:

Suppose that we want to know how many times we have sold each product. In other words, for each sku value in the products table, we want to know the number of times it occurs in the sales table. We might start out with a query like this:

```
select products.name, products.sku, count(*) as num
  from products join sales
    on products.sku = sales.sku
  group by products.sku;
```

But this query might not do exactly what we want. If a particular sku has never been sold — if there are no entries for it in the sales table — then this query will not return a row for it at all.

If we wanted to see a row with the number zero in it, we’ll be disappointed!

However, there is a way to get the database to give us a count with a zero in it. To do this, we’ll need to change two things about this query —

```
select products.name, products.sku, count(sales.sku) as num
  from products left join sales
    on products.sku = sales.sku
  group by products.sku;
```

This query will give us a row for every product in the products table, even the ones that have no sales in the sales table.

What’s changed? First, we’re using count(sales.sku) instead of count(*). This means that the database will count only rows where sales.sku is defined, instead of all rows.

Second, we’re using a left join instead of a plain join.

### Um, so what’s a left join?
SQL supports a number of variations on the theme of joins. The kind of join that you have seen earlier in this course is called an inner join, and it is the most common kind of join — so common that SQL doesn’t actually make us say "inner join" to do one.

But the second most common is the left join, and its mirror-image partner, the right join. The words “left” and “right” refer to the tables to the left and right of the join operator. (Above, the left table is products and the right table is sales.)

A regular (inner) join returns only those rows where the two tables have entries matching the join condition. A left join returns all those rows, plus the rows where the left table has an entry but the right table doesn’t. And a right join does the same but for the right table.

(Just as “join” is short for “inner join”, so too is “left join” actually short for “left outer join”. But SQL lets us just say “left join”, which is a lot less typing. So we’ll do that.)

### Counting what isn't there - Solution
Here's the original query from the quiz again —

```
select programs.name, count(*) as num
      from programs join bugs
        on programs.filename = bugs.filename
      group by programs.name
      order by num;
```

And here's one possible corrected version:

```
select programs.name, count(bugs.filename) as num
      from programs left join bugs
        on programs.filename = bugs.filename
      group by programs.name
      order by num;
```

Something to watch out for: What do you put in the count aggregation? If you leave it as count(*) or use a column from the programs table, your query will count entries that don't have bugs as well as ones that do.

In order to correctly report a zero for programs that don't have any entries in the bugs table, you have to use a column from the bugs table as the argument to count. For instance, count(bugs.filename) will work, and so will count(bugs.description).

## 11.12 Some DB-API's

Database System | DB-API Module
--------------- | -------------
SQLite | sqlite3
PostgreSQL | psycopg2
ODBC | pyodbc
MySQL | mysql.connector

## 11.18 Views

A view is a select query stored in the database in a way that lets you use it like a table

Syntax:
Create view viewname as select