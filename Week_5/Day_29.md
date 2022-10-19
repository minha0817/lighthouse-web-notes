# W05D02 - Database Design

### Primary Key
- A way of uniquely identifying a particular record within a table 
- Must be unique (within the table) and can never be null
- The usual data type is auto-incrementing integer (`INTEGER` or `BIGINT`)
- A Primary Key stored in another table is known as a `Foreign Key`
- The Primary Key and Foreign Key **MUST** be the same data type
### Foreign key
- A field in one table that refers to a primary key in another table.
- It's how we model relationships in a relational database.
- Foreign key goes on the many side on one to many relationship type.
### Naming Conventions
- Table and field names are written in `snake_case`
- Table names are always pluralized (students, teachers, assignments)
- The primary key for each table will simply be called `id`
- A foreign key is made up of the singular of the primary keys table and the suffix `_id` (eg. `user_id` is the foreign key for the `id` field in the `users` table)
### Data Types
- Each field in a table **must** have a data type defined for it
- The data type tells the database how much room to set aside to store the value _and_ allows the database to perform type validation on data before insertion (to protect the data integrity of the table)
- Choosing the perfect data type is less of a concern nowadays because memory is now comparably cheap
### Relationship Types
- **One-to-One**: One record in the first table is related to one (and only one) record in the second table
- **One-to-Many**: One record in the first table is related to one or more records in the second table
- **Many-to-Many**: One or more records in the first table are related to one or more records in the second table
- There are no direct many-to-many relationships -> only multiple one-to-many relationships using a join table.
- It could be argued that there is really only one relationship type: _One-to-Many_ as One-to-One's are extremely rare and Many-to-Many's are implemented using two _One-to-Many's_
### Data Normalization 
- Why we normalize database? to enforce data integrity, reduce duplication and make it easier to manage our data.
- How? By making another table (usually)
### Design Concepts
- Make fields required based on the records state upon initial creation (remember that additional data can be added to a record after it has been created)
- Intelligent default values can be set for fields (such as the current timestamp for a `created_on` field)
- Don't use calculated fields (a field that can be derived from one or more other fields, such as `full_name` is a combination of `first_name` and `last_name`)
- Pull repeated values out to their own table and make reference to them with a foreign key
- Try not to delete anything (use a boolean flag instead to mark a record as active or inactive)
- Consider using a `type` field instead of using two (or more) tables to store very similar data (eg. create an `orders` table with an `order_type` field instead of a `purchase_orders` and a `sales_orders` table)
### Entity Relationship Diagram (ERD)
- A visual depiction of the database tables and how they are related to each other
- Extremely useful for reasoning about how the database should be structured
- Can be created using pen and paper, a whiteboard, or using an online application
### Task: Convert Two Spreadsheets into an ERD
- [Gist with instruction](https://gist.github.com/andydlindsay/20e7305e853bad7b587f294b054cf8de)
![Authors/Publishers ERD](https://raw.githubusercontent.com/ChristianNally/web-2022-Sep-19-west-samples/main/w05d2/w05d2%20lecture.drawio.png)
### Student Suggestion: Coffee Distributor
We created an ERD for a fictional coffee distributor:
![Coffee Distributor](https://raw.githubusercontent.com/ChristianNally/web-2022-Sep-19-west-samples/main/w05d2/coffee%20distributor.drawio.png)

### Example
```sql
CREATE TABLE students (
  id SERIAL PRIMARY KEY NOT NULL,
  name varchar(255) NOT NULL,
  email varchar(255),
  phone varchar(32),
  github varchar(250),
  start_date DATE,
  end_date DATE,
  cohort_id INTEGER REFERENCES cohorts(id) ON DELETE CASCADE
);

SELECT DISTINCT teachers.name as teacher, cohorts.name as cohort,
count(assistance_requests.*) as total_assistances
FROM teachers
JOIN assistance_requests ON teachers.id = teacher_id
JOIN students ON students.id = student_id
JOIN cohorts ON cohorts.id = cohort_id
WHERE cohorts.name = 'JUL02'
GROUP BY teachers.name, cohorts.name
ORDER BY teacher;

SELECT cohorts.name, avg(completed_at - started_at) as average_assistance_time 
FROM assistance_requests
JOIN students ON students.id = student_id
JOIN cohorts ON cohorts.id = cohort_id
GROUP BY cohorts.name
ORDER BY average_assistance_time DESC
LIMIT 1;
```
### Useful Links
* [Database Normalization](https://en.wikipedia.org/wiki/Database_normalization)
* [Postgres Data Types](http://www.postgresqltutorial.com/postgresql-data-types/)
* [Relationship Types](http://etutorials.org/SQL/Database+design+for+mere+mortals/Part+II+The+Design+Process/Chapter+10.+Table+Relationships/Types+of+Relationships/)
* [draw.io (online ERD)](https://www.draw.io/)