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

The process of defining the tables for a database begins with a review of the Preliminary Field List. Your objective is to identify subjects that are implied by the fields on the list.
Create unique and descriptive table names that are meaningful to the entire organization. Probably the most vague and ambiguous name you could assign to a table is 'Miscellaneous' - it doesn't identify a single subject.

Indicating the table types. Recall that there are four classifications you can use to identify the table: data, linking, subset, validation.

Resolve multipart fields by identifying the distinct items within the field's value and treating each item as an individual field.

Redundant data is a value that is repeated in a field as a result of the field's participation in relating two tables or as a result of some field or table anomaly.  In the first instance, the redundant data is appropriate; by definition, a field used to relate one table to another will contain redundant data. Redundant data is eentirely unacceptable in the second instance, however, because it poses problems with data consistency and data integrity; therefore, you should always strive to keep redundant data to an absolute minimum. 

---

## Keys

There are four main types of keys: candidate, primary, foreign, non-keys. A primary key field exclusively identifies the table throughout the database structure and helps establish relationships with other tables.

---

## Field Specifications

Field level integrity warrants the following:

* The identity and purpose of a field is clear, and all of the tables in which it appears are properly identified.
* Field definitions are consistent throughout the database.
* The values of a field are consistent and valid.
* The types of modifications, comparisons, and operations that can be applied to the values in the field are clearly specified.

---

## Table Relationships

A properly defined relationship ensures relationship level integrity, which guarantees that a relationship itself is relaible and sound.



Types of relatonships: one to one, one to many, many to many. Some examples:

* One to one: Am employees table that get's mapped one to one on a compensation table.

* One to many: One trade can have many fills.

* Many to many: Suppose that we have both a students and a classes table. Each class can have many students and each student can have many classes.

A many to many relationship has an inherent peculiarity that you must address before you can effectively use the data from the tables involved in the relationship: How do you easily associate records as there is no actual connection?

You use a primay key and a foreign key to establish the connection between tables participating in a one to one or one to many relationship.

You establish a many to many relationship with a linking table. The linking table helps to keep redundant data to an absolute minimum.

Regarding self referencing relationships: you use a primary key and a foreign key to establish these self referencing relationships. The difference here, however, is that the foreign key will reside in the same table as the primary key to which it refers. Consider a members table as a one to one self referencing relationship because a given member can sponsor only one other member within the organization.  Because the sponsor id field draws its values exclusively from the member id field, it acts as the foreign key for the relationship.

A many to many relf referencing relationship might be a parts table where each part can consist of combinations of other parts. We could use a part components linking table where the part id and associated compontent part ids are foreign keys from the parts table.

---
## Business Rules
A business rule is a statement that imposes some form of constraint on a specific aspect of the database. One example might be: a ship date cannto be prior to an order date. In the context of Python programming and sqlalchemy we have sqlalchemy.CheckConstraint.

A validation table, also known as a lookup table, stores data that you specifically use for data integrity. Validation tables typically consist of a primary key and a non-key field.

---
## Views
The tables and views that comprise a given view are known as the view's base tables. A view is 'virtual' because it draws data from the base tables rather than storing data on its own. The only information about a view that is stored in the database is it's structure. Why use views:
* Work with data from multiple tables simultaneously.
* They reflect the most current information.
* You can customize them to the specific needs of an individual or group of individuals.
* We can include validation views.

---
## Reviewing Data Integrity
You want to make certain that the data integrity you've been so careful to establish is absolutely as sound as possible. You can take a modular approach of overall data integrity: table level, field level, relationship level integrity and business rules. Database documentation is also important now that we are reaching the end of our design process.

---
# Other Topics
## Bad Design - What Not to Do
