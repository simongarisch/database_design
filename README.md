# Database Design

## The design process - conceptual overview (7 steps)
Only if you follow through the full, unabbreviated design process are you assured a sound structure and data integrity.
However, the process is never really complete because the database structure will always need refinement as your organization evolves. 
1. Defining a mission statement and objectives.
2. Analyzing the current database (if one exists).

3. Creating the data structures.
  * Tables will be the first structures defined. Establish eash subject as a table and associated fields.
  * Review to ensure each table relates to only one subject and doesn't have duplicated fields.
  * Each field should only store a single value and not be multipart / multivalued.
  * Ensure each table has a properly defined primary key which uniquely identifies each record.
  * Establish specs for each field.
  * Review with users for possible refinements.
  
4. Determining and Establishing table relationships
  * Identify relationships.
  * Establish logical connections through a primary key or linking table.
  * Determine the participation and degree of participation for the tables in each relationship.

5. Determining and defining business rules.
  * Collect relationship rules.
  * Create [validation](https://www.databasejournal.com/features/mssql/article.php/3811831/Using-Check-Constraints-to-Validate-Data-in-SQL-Server.htm) tables.
  
6. Determining and defining views.

7. Reviewing data integrity.

---

## Starting the process
This is very much focussed on interviews and creating a mission statement.
Some interview techniques are described.
People are likely to have different opinions and data needs regarding the business workflow / database purpose.
Mission objectives represent the tasks performed against the data in the database, and you define them after the mission statement.

---

## Analyzing the current database
To determine where you should go, you must first understand where you are.
This could even be a paper based database or some other crude collection of files.
If your analysis reveals that the current database is poorly designed, you can take precautions to ensure that you don't make the same mistakes in the new database. Do not adopt the current database structure as the basis for the new database structure.
Also consider any future requirements the users may have.

---

## Establishing table structures



