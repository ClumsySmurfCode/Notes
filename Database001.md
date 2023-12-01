# DataBase 

![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/27867e49-4af2-4ef1-be64-761ef10b69c8)
<hr>

### Database integrity and Validation 
- Data Constraint
  PK, FK, Unique, NOT NULL, NULL, DEFAULT, CHECK
### Relationship 
- Optionality and Cardinality

                      1 .. N
            Optionality .. Cardinality


In the context of Relational Database Management Systems (RDBMS), optionality and cardinality refer to the relationships between tables. Let's break down these concepts in simple language:

#### Optionality:
Definition: Optionality describes whether a relationship between two tables is mandatory or optional.
Example: Consider two tables - Students and Courses. If a student can be enrolled in zero or more courses, the relationship between the two tables is optional. On the other hand, if every student must be enrolled in at least one course, the relationship is mandatory.
#### Cardinality:
Definition: Cardinality specifies the number of instances of one entity that can be related to a single instance of another entity.
Example: Taking the same Students and Courses example, let's say a student can be enrolled in multiple courses, but a course can have multiple students as well. This is a many-to-many cardinality. Conversely, if each student can only be enrolled in one course (but a course can have many students), it's a many-to-one cardinality. If each student can be enrolled in multiple courses, but each course can only have one student, it's a one-to-many cardinality.

<hr>

![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/54b60f27-25a3-405c-940b-05e08ec4c710)
