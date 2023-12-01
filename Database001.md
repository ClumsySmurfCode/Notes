# DataBase 

![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/27867e49-4af2-4ef1-be64-761ef10b69c8)
<hr>

# Database integrity and Validation 
- Data Constraint
  PK, FK, Unique, NOT NULL, NULL, DEFAULT, CHECK
## - Relationship 
### Optionality and Cardinality

                      1 .. N
            Optionality .. Cardinality


In the context of Relational Database Management Systems (RDBMS), optionality and cardinality refer to the relationships between tables. Let's break down these concepts in simple language:

##### Optionality:
- Definition: Optionality describes whether a relationship between two tables is mandatory or optional.
Example: Consider two tables - Students and Courses. If a student can be enrolled in zero or more courses, the relationship between the two tables is optional. On the other hand, if every student must be enrolled in at least one course, the relationship is mandatory.
##### Cardinality:
- Definition: Cardinality specifies the number of instances of one entity that can be related to a single instance of another entity.
Example: Taking the same Students and Courses example, let's say a student can be enrolled in multiple courses, but a course can have multiple students as well. This is a many-to-many cardinality. Conversely, if each student can only be enrolled in one course (but a course can have many students), it's a many-to-one cardinality. If each student can be enrolled in multiple courses, but each course can only have one student, it's a one-to-many cardinality.

### ONE to MANY
A "one-to-many" relationship describes a situation where one record in one table is related to multiple records in another table.
It's a common and fundamental type of relationship in databases.

##### DataBase implementation
- In the database, this relationship is typically established through foreign keys.
- The Teachers table might have a primary key (like TeacherID), and the Students table would have a foreign key (like TeacherID) linking back to the Teachers table.

##### Example : 
In a "one-to-many" relationship, one teacher can have many students, but each student has only one teacher.
So, a teacher is associated with multiple students, but each student is linked to only one teacher.

### ONE to ONE
A "one-to-one" relationship describes a situation where one record in one table is directly related to only one record in another table, and vice versa.
It's a less common but still important type of relationship in databases

##### DataBase implementation
- In the database, this relationship is often established using primary and foreign keys.
- For example, the People table might have a primary key (like PersonID), and the Passports table would have a foreign key (like PersonID) linking back to the People table.

##### Example :
In a "one-to-one" relationship, each person has only one passport, and each passport is issued to only one person.
So, if you have a record in the People table, there is exactly one corresponding record in the Passports table, and vice versa.

### MANY to MANY
A "many-to-many" relationship describes a situation where multiple records in one table are associated with multiple records in another table.
It's a common and flexible type of relationship in databases.

##### DataBase implementation
- In the database, this relationship is often implemented using three tables: the two main tables (Students and Courses) and a junction table (Enrollments).
- The junction table contains foreign keys that link back to both the Students and Courses tables, establishing the connections.
  
![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/8d0af74c-ecb5-468a-a3b8-c124af7cfda5)

##### Real-world Analogy
Think of it like students and courses in a school. Each student can take multiple courses, and each course can have multiple students enrolled.

##### Example :
- In a "many-to-many" relationship, each student can be enrolled in multiple courses, and each course can have multiple students.
- So, you can have a student associated with many courses, and a course associated with many students.

### Decomplexify
Reference: https://www.youtube.com/@decomplexify
1NF,2NF, 3NF, BCNF, 4NF, 5NF 

#### First Normal Form (1NF):

- Idea: Ensure that each column in a table contains atomic (indivisible) values, and there are no repeating groups or arrays of data.
- Example: If you have a column for phone numbers, make sure it holds only one phone number, not a list of numbers.



#### Second Normal Form (2NF):

- Idea: Meet 1NF and ensure that all non-key attributes are fully functionally dependent on the primary key.
- Example: If you have a composite primary key (made up of multiple columns), make sure every other column depends on the entire composite key, not just part of it.

#### Third Normal Form (3NF):

- Idea: Meet 2NF and remove transitive dependencies. In simpler terms, make sure non-key columns don't depend on other non-key columns.
- Example: If you have a table with employee information and the department manager is listed, the department manager's phone number should not be in the same table. Create a separate table for department information.

#### Boyce-Codd Normal Form (BCNF):

- Idea: Meet 3NF and ensure that every determinant (a column on which another column is functionally dependent) is a candidate key.
- Example: If a table has multiple candidate keys, make sure that each non-prime attribute is fully functionally dependent on every superkey.

#### Fourth Normal Form (4NF):

- Idea: Meet BCNF and eliminate multivalued dependencies.
- Example: If you have a table tracking courses and instructors, ensure that instructor information is not repeated for each course. Instead, have a separate table for instructors

#### Fifth Normal Form (5NF):

- Idea: Meet 4NF and eliminate join dependencies.
- Example: If you have a table with information about employees and their projects, ensure that each fact (e.g., a project's start date) is stored in only one table.


## 1. First Normal Form (1NF):
Definition:

A table is in 1NF if it contains only atomic (indivisible) values, and there are no repeating groups or arrays of data.
Each column must have a single, indivisible value.

Example:
If you have a table of students with a column for "Phone Numbers" that can contain multiple phone numbers separated by commas, it's not in 1NF. To bring it to 1NF, you would create a new table for phone numbers, linking them to the student through a foreign key.

## 2. Second Normal Form (2NF):
Definition:
A table is in 2NF if it is in 1NF and all non-key attributes are fully functionally dependent on the primary key.
In simpler terms, there should be no partial dependencies.

Example:
If you have a composite primary key (e.g., StudentID and CourseID) and a column "Grade," the Grade should depend on both StudentID and CourseID. If it depends only on StudentID, it's a partial dependency and violates 2NF.

##  3. Third Normal Form (3NF):
Definition:
A table is in 3NF if it is in 2NF, and there are no transitive dependencies.
Non-key attributes should not depend on other non-key attributes.

Example:
If you have a table with columns StudentID, CourseID, ProfessorName, where ProfessorName depends on CourseID, it violates 3NF. The ProfessorName should be in a separate table with CourseID as its primary key.

## BCNF (Boyce-Codd Normal Form):
Definition:
A table is in BCNF if it is in 3NF and for every non-trivial functional dependency, the left-hand side is a superkey.

Example:
If you have a table with columns StudentID, CourseID, ProfessorName, and ProfessorName depends only on StudentID, it violates BCNF. To achieve BCNF, separate out the Professor information into a table with StudentID as the primary key.

## 4. Fourth Normal Form (4NF):
Definition:
A table is in 4NF if it is in BCNF and has no multi-valued dependencies.

Example:
If you have a table with columns StudentID, CourseID, ProfessorName, and CourseMaterial, where CourseMaterial depends on CourseID, it violates 4NF. To achieve 4NF, move CourseMaterial to a separate table with CourseID as its primary key.

## 5. Fifth Normal Form (5NF):
Definition:
A table is in 5NF if it is in 4NF and there are no join dependencies.

Example:
If you have a table with columns StudentID, CourseID, ProfessorName, and OfficeLocation, where OfficeLocation depends on ProfessorName, it violates 5NF. To achieve 5NF, separate out the Professor information into a table with ProfessorName as its primary key.
<hr>

![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/54b60f27-25a3-405c-940b-05e08ec4c710)
