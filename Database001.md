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

<hr>

![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/54b60f27-25a3-405c-940b-05e08ec4c710)
