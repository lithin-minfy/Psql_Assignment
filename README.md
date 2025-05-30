# Psql_Assignment

C:\Users\Minfy>psql --version
psql (PostgreSQL) 17.5

C:\Users\Minfy>psql -U postgres
Password for user postgres:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

postgres=# CREATE USER uni_admin WITH PASSWORD '1234567890'
postgres-# CREATE USER uni_admin WITH PASSWORD '1234567890';
ERROR:  syntax error at or near "CREATE"
LINE 2: CREATE USER uni_admin WITH PASSWORD '1234567890';
        ^
postgres=# \q

C:\Users\Minfy>psql -U postgres
Password for user postgres:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

postgres=# CREATE USER uni_admin WITH PASSWORD '1234567890';
CREATE ROLE
postgres=# CREATE DATABASE uni_db OWNER uni_admin;
CREATE DATABASE
postgres=# GRANT ALL PRIVILEGES ON DATABASE uni_db TO uni_admin;
GRANT
postgres=# //q
postgres-# \q

C:\Users\Minfy>psql -U university_admin -d university_db
Password for user university_admin:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "university_admin"

C:\Users\Minfy>psql -U university_admin -d university_db
Password for user university_admin:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "university_admin"

C:\Users\Minfy> psql -U postgres
Password for user postgres:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

postgres=# ALTER USER uni_admin WITH PASSWORD '12345';
ALTER ROLE
postgres=# GRANT ALL PRIVILEDGES ON DATABASE uni_db TO uni_admin;
ERROR:  syntax error at or near "PRIVILEDGES"
LINE 1: GRANT ALL PRIVILEDGES ON DATABASE uni_db TO uni_admin;
                  ^
postgres=# GRANT ALL PRIVILEGES ON DATABASE uni_db TO uni_admin;
GRANT
postgres=# /q
postgres-# \q

C:\Users\Minfy>psql -U uni_admin -d uni_db;
Password for user uni_admin:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  database "uni_db;" does not exist

C:\Users\Minfy>psql -U uni_admin -d uni_db
Password for user uni_admin:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

uni_db=> CREATE TABLE students(
uni_db(>
uni_db(>
uni_db(>
uni_db(> \\q
invalid command \
Try \? for help.
uni_db(> \q

C:\Users\Minfy>psql -U uni_admin -d uni_db
Password for user uni_admin:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

uni_db=> CREATE TABLE students(
uni_db(> student_id INTEGER,
uni_db(> first_name VARCHAR(50),
uni_db(> last_name VARCHAR(50),
uni_db(> email VARCHAR(50),
uni_db(> dob DATE);
CREATE TABLE
uni_db=> \\dt
invalid command \
Try \? for help.
uni_db=> \\d
invalid command \
Try \? for help.
uni_db=> \d
           List of relations
 Schema |   Name   | Type  |   Owner
--------+----------+-------+-----------
 public | students | table | uni_admin
(1 row)


uni_db=> \dt
           List of relations
 Schema |   Name   | Type  |   Owner
--------+----------+-------+-----------
 public | students | table | uni_admin
(1 row)


uni_db=> ALTER TABLE students ADD COLUMN enrollment_date DATE
uni_db-> ALTER TABLE students ADD COLUMN enrollment_date DATE;
ERROR:  syntax error at or near "ALTER"
LINE 2: ALTER TABLE students ADD COLUMN enrollment_date DATE;
        ^
uni_db=> ALTER TABLE students ADD COLUMN enrollment_date DATE;
ALTER TABLE
uni_db=> ALTER TABLE students DROP COLUMN enrollment_date DATE;
ERROR:  syntax error at or near "DATE"
LINE 1: ALTER TABLE students DROP COLUMN enrollment_date DATE;
                                                         ^
uni_db=> ALTER TABLE students DROP COLUMN enrollment_date;
ALTER TABLE
uni_db=> ALTER TABLE students ALTER COLUMN email TYPE VARCHAR(150);
ALTER TABLE
uni_db=> ALTER TABLE students ADD CONSTRAINT unique_email UNIQUE (email);
ALTER TABLE
uni_db=> ALTER TABLE students ADD COLUMN phone_number TYPE VARCHAR(15);
ERROR:  syntax error at or near "VARCHAR"
LINE 1: ALTER TABLE students ADD COLUMN phone_number TYPE VARCHAR(15...
                                                          ^
uni_db=> ALTER TABLE students ADD COLUMN phone_number VARCHAR(15);
ALTER TABLE
uni_db=> ALTER TABLE students DROP COLUMN phone_number VARCHAR(15);
ERROR:  syntax error at or near "VARCHAR"
LINE 1: ALTER TABLE students DROP COLUMN phone_number VARCHAR(15);
                                                      ^
uni_db=> ALTER TABLE students DROP COLUMN phone_numbER;
ALTER TABLE
uni_db=> ALTER TABLE students DROP COLUMN phone_number;
ERROR:  column "phone_number" of relation "students" does not exist
uni_db=> ALTER TABLE students DROP COLUMN phone_number;
ERROR:  column "phone_number" of relation "students" does not exist
uni_db=> INSERT INTO students(student_id,first_name,last_name,email,dob)
uni_db-> VALUES(1,'Lithin','varma','lithin.varma@gmail.com','2003-09-15');
INSERT 0 1
uni_db=> VALUES(2,'Madhu','kumar','madhu.kumar@gmail.com','2003-07-16');
 column1 | column2 | column3 |        column4        |  column5
---------+---------+---------+-----------------------+------------
       2 | Madhu   | kumar   | madhu.kumar@gmail.com | 2003-07-16
(1 row)


uni_db=> INSERT INTO students(student_id,first_name,last_name,email,dob)
uni_db-> VALUES(3,'john','fancis','john.francis@gmail.com','2003-10-10'),
uni_db-> VALUES(4,'abhi','raj','abhi@gmail.com','2003-11-20'),
uni_db-> VALUES(5,'rahul','kumar','rahul@gmail.com','2003-12-28');
ERROR:  syntax error at or near "VALUES"
LINE 3: VALUES(4,'abhi','raj','abhi@gmail.com','2003-11-20'),
        ^
uni_db=> VALUES(4,'abhi','raj','abhi@gmail.com','2003-11-20');
 column1 | column2 | column3 |    column4     |  column5
---------+---------+---------+----------------+------------
       4 | abhi    | raj     | abhi@gmail.com | 2003-11-20
(1 row)


uni_db=> DELETE FROM students;
DELETE 1
uni_db=> SELECT * FROM students;
 student_id | first_name | last_name | email | dob
------------+------------+-----------+-------+-----
(0 rows)


uni_db=> INSERT INTO students(student_id,first_name,last_name,email,dob)
uni_db-> VALUES(1,'rahul','chow','rahul.chow@gmail.com','2003-12-10'),
uni_db-> VALUES(2,'Lithin','varma','lithin.varma@gmail.com','2003-09-15'),
uni_db-> VALUES(3,'john','francis','john.francis@gmail.com','2002-12-04'),
uni_db-> VALUES(4,'madhu','kumar','madhu.kumar@gmail.com','2002-06-30'),
uni_db-> VALUES(5,'Jeet','singh','jeet.singh@gmail.com','2003-07-14');
ERROR:  syntax error at or near "VALUES"
LINE 3: VALUES(2,'Lithin','varma','lithin.varma@gmail.com','2003-09-...
        ^
uni_db=> INSERT INTO students(student_id, first_name, last_name, email, dob)
uni_db-> VALUES
uni_db->   (1, 'rahul', 'chow', 'rahul.chow@gmail.com', '2003-12-10'),
uni_db->   (2, 'Lithin', 'varma', 'lithin.varma@gmail.com', '2003-09-15'),
uni_db->   (3, 'john', 'francis', 'john.francis@gmail.com', '2002-12-04'),
uni_db->   (4, 'madhu', 'kumar', 'madhu.kumar@gmail.com', '2002-06-30'),
uni_db->   (5, 'Jeet', 'singh', 'jeet.singh@gmail.com', '2003-07-14');
INSERT 0 5
uni_db=> SELECT * FROM students;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          1 | rahul      | chow      | rahul.chow@gmail.com   | 2003-12-10
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
          4 | madhu      | kumar     | madhu.kumar@gmail.com  | 2002-06-30
          5 | Jeet       | singh     | jeet.singh@gmail.com   | 2003-07-14
(5 rows)


uni_db=> INSERT INTO students(student_id, first_name, last_name, dob)
uni_db-> VALUES(6,'abhi','kumar','2002-02-10');
INSERT 0 1
uni_db=> SELECT * FROM students;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          1 | rahul      | chow      | rahul.chow@gmail.com   | 2003-12-10
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
          4 | madhu      | kumar     | madhu.kumar@gmail.com  | 2002-06-30
          5 | Jeet       | singh     | jeet.singh@gmail.com   | 2003-07-14
          6 | abhi       | kumar     |                        | 2002-02-10
(6 rows)


uni_db=> SELECT * FROM student
uni_db-> WHERE student_id=2;
ERROR:  relation "student" does not exist
LINE 1: SELECT * FROM student
                      ^
uni_db=> SELECT * FROM student,
uni_db-> WHERE student_id=2;
ERROR:  syntax error at or near "WHERE"
LINE 2: WHERE student_id=2;
        ^
uni_db=> SELECT * FROM student WHERE student_id=2;
ERROR:  relation "student" does not exist
LINE 1: SELECT * FROM student WHERE student_id=2;
                      ^
uni_db=> SELECT * FROM students WHERE student_id=2;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
(1 row)


uni_db=> SELECT * FROM students WHERE dob>'2003-01-01';
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          1 | rahul      | chow      | rahul.chow@gmail.com   | 2003-12-10
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
          5 | Jeet       | singh     | jeet.singh@gmail.com   | 2003-07-14
(3 rows)


uni_db=> SELECT * FROM students WHERE dob<'2003-01-01';
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
          4 | madhu      | kumar     | madhu.kumar@gmail.com  | 2002-06-30
          6 | abhi       | kumar     |                        | 2002-02-10
(3 rows)


uni_db=> SELECT * FROM students WHERE first_name LIKE 'B%' OR first_name LIKE 'C%';
 student_id | first_name | last_name | email | dob
------------+------------+-----------+-------+-----
(0 rows)


uni_db=> SELECT * FROM students WHERE email '%gmail.com';
ERROR:  type "email" does not exist
LINE 1: SELECT * FROM students WHERE email '%gmail.com';
                                     ^
uni_db=> SELECT * FROM students WHERE email LIKE '%gmail.com';
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          1 | rahul      | chow      | rahul.chow@gmail.com   | 2003-12-10
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
          4 | madhu      | kumar     | madhu.kumar@gmail.com  | 2002-06-30
          5 | Jeet       | singh     | jeet.singh@gmail.com   | 2003-07-14
(5 rows)


uni_db=> SELECT * FROM students WHERE email IS NULL;
 student_id | first_name | last_name | email |    dob
------------+------------+-----------+-------+------------
          6 | abhi       | kumar     |       | 2002-02-10
(1 row)


uni_db=> SELECT * FROM students WHERE email IS NOT NULL;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          1 | rahul      | chow      | rahul.chow@gmail.com   | 2003-12-10
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
          4 | madhu      | kumar     | madhu.kumar@gmail.com  | 2002-06-30
          5 | Jeet       | singh     | jeet.singh@gmail.com   | 2003-07-14
(5 rows)


uni_db=> UPDATE students
uni_db-> SET email = 'rahul.gmail.com'
uni_db-> WHERE student_id IS 1;
ERROR:  syntax error at or near "1"
LINE 3: WHERE student_id IS 1;
                            ^
uni_db=> UPDATE students
uni_db-> SET email = 'rahul.gmail.com'
uni_db-> WHERE student_id = 1;
UPDATE 1
uni_db=> UPDATE students
uni_db-> SET dob = '2002-05-16'
uni_db-> WHERE student_id = 4;
UPDATE 1
uni_db=> UPDATE students
uni_db-> SET email = 'abhi.kumar@gmail.com'
uni_db-> WHERE student_id = 6;
UPDATE 1
uni_db=> SELECT * FROM students ORDER BY last_name ASC;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          1 | rahul      | chow      | rahul.gmail.com        | 2003-12-10
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
          4 | madhu      | kumar     | madhu.kumar@gmail.com  | 2002-05-16
          6 | abhi       | kumar     | abhi.kumar@gmail.com   | 2002-02-10
          5 | Jeet       | singh     | jeet.singh@gmail.com   | 2003-07-14
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
(6 rows)


uni_db=> SELECT * FROM students ORDER BY last_name DESC;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
          5 | Jeet       | singh     | jeet.singh@gmail.com   | 2003-07-14
          4 | madhu      | kumar     | madhu.kumar@gmail.com  | 2002-05-16
          6 | abhi       | kumar     | abhi.kumar@gmail.com   | 2002-02-10
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
          1 | rahul      | chow      | rahul.gmail.com        | 2003-12-10
(6 rows)


uni_db=> SELECT * FROM students ORDER BY dob ASC;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          6 | abhi       | kumar     | abhi.kumar@gmail.com   | 2002-02-10
          4 | madhu      | kumar     | madhu.kumar@gmail.com  | 2002-05-16
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
          5 | Jeet       | singh     | jeet.singh@gmail.com   | 2003-07-14
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
          1 | rahul      | chow      | rahul.gmail.com        | 2003-12-10
(6 rows)


uni_db=> SELECT * FROM students ORDER BY last_name DESC, first_name ASC;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
          5 | Jeet       | singh     | jeet.singh@gmail.com   | 2003-07-14
          6 | abhi       | kumar     | abhi.kumar@gmail.com   | 2002-02-10
          4 | madhu      | kumar     | madhu.kumar@gmail.com  | 2002-05-16
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
          1 | rahul      | chow      | rahul.gmail.com        | 2003-12-10
(6 rows)


uni_db=> SELECT * FROM students ORDER BY student_id LIMIT 2 OFFSET 2;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
          4 | madhu      | kumar     | madhu.kumar@gmail.com  | 2002-05-16
(2 rows)


uni_db=> SELECT * FROM students ORDER BY student_id ASC LIMIT 2;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          1 | rahul      | chow      | rahul.gmail.com        | 2003-12-10
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
(2 rows)


uni_db=> SELECT * FROM students ORDER BY student_id DESC LIMIT 2;
 student_id | first_name | last_name |        email         |    dob
------------+------------+-----------+----------------------+------------
          6 | abhi       | kumar     | abhi.kumar@gmail.com | 2002-02-10
          5 | Jeet       | singh     | jeet.singh@gmail.com | 2003-07-14
(2 rows)


uni_db=> SELECT * FROM students ORDER BY student_id OFFSET 1;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
          4 | madhu      | kumar     | madhu.kumar@gmail.com  | 2002-05-16
          5 | Jeet       | singh     | jeet.singh@gmail.com   | 2003-07-14
          6 | abhi       | kumar     | abhi.kumar@gmail.com   | 2002-02-10
(5 rows)


uni_db=> SELECT * FROM students ORDER BY student_id LIMIT 2 OFFSET 1;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
(2 rows)


uni_db=> INSERT INTO students(student_id,first_name,last_name,email,dob)
uni_db-> VALUES(2,'Lithin','varma',lithin.varma@gmail.com,'2003-09-15');
ERROR:  missing FROM-clause entry for table "lithin"
LINE 2: VALUES(2,'Lithin','varma',lithin.varma@gmail.com,'2003-09-15...
                                  ^
uni_db=> INSERT INTO students(student_id,first_name,last_name,email,dob)
uni_db-> VALUES(2,'Lithin','varma','lithin.varma@gmail.com','2003-09-15');
ERROR:  duplicate key value violates unique constraint "unique_email"
DETAIL:  Key (email)=(lithin.varma@gmail.com) already exists.
uni_db=> SELECT COUNT(email) AS students_with_email FROM students;
 students_with_email
---------------------
                   6
(1 row)


uni_db=> SELECT DISTINCT COUNT(last_name) AS unique_names FROM students;
 unique_names
--------------
            6
(1 row)


uni_db=> INSERT INTO students(student_id,first_name,last_name,email,dob)
uni_db-> VALUES(2,'Lithin','varma','lithin@gmail.com','2003-09-15');
INSERT 0 1
uni_db=> SELECT * FROM students;
 student_id | first_name | last_name |         email          |    dob
------------+------------+-----------+------------------------+------------
          2 | Lithin     | varma     | lithin.varma@gmail.com | 2003-09-15
          3 | john       | francis   | john.francis@gmail.com | 2002-12-04
          5 | Jeet       | singh     | jeet.singh@gmail.com   | 2003-07-14
          1 | rahul      | chow      | rahul.gmail.com        | 2003-12-10
          4 | madhu      | kumar     | madhu.kumar@gmail.com  | 2002-05-16
          6 | abhi       | kumar     | abhi.kumar@gmail.com   | 2002-02-10
          2 | Lithin     | varma     | lithin@gmail.com       | 2003-09-15
(7 rows)


uni_db=> SELECT last_name,COUNT(*) AS no_of_students
uni_db-> FROM students
uni_db-> GROUP BY last_name
uni_db-> ;
 last_name | no_of_students
-----------+----------------
 francis   |              1
 kumar     |              2
 singh     |              1
 chow      |              1
 varma     |              2
(5 rows)


uni_db=> SELECT last_name,COUNT(*) AS no_of_students
uni_db-> FROM students
uni_db-> GROUP BY last_name
uni_db-> HAVING COUNT(*)>1
uni_db-> ;
 last_name | no_of_students
-----------+----------------
 kumar     |              2
 varma     |              2
(2 rows)


uni_db=> SELECT DISTINCT COUNT(first_name) FROM students;
 count
-------
     7
(1 row)


uni_db=> SELECT COUNT(DISTINCT first_name) FROM students;
 count
-------
     6
(1 row)


uni_db=> SELECT last_name,COUNT(*) AS no_of_students_BORN_IN_EACHYEAR
uni_db-> FROM students
uni_db-> GROUP BY dob;
ERROR:  column "students.last_name" must appear in the GROUP BY clause or be used in an aggregate function
LINE 1: SELECT last_name,COUNT(*) AS no_of_students_BORN_IN_EACHYEAR
               ^
uni_db=> SELECT dob,COUNT(*) AS no_of_students_BORN_IN_EACHYEAR
uni_db-> FROM students
uni_db-> GROUP BY dob;
    dob     | no_of_students_born_in_eachyear
------------+---------------------------------
 2003-12-10 |                               1
 2003-09-15 |                               2
 2003-07-14 |                               1
 2002-12-04 |                               1
 2002-05-16 |                               1
 2002-02-10 |                               1
(6 rows)


uni_db=> SELECT extract(year from dob) AS Year,COUNT(*) AS no_of_students_BORN_IN_EACHYEAR
uni_db-> FROM students
uni_db-> GROUP BY dob;
 year | no_of_students_born_in_eachyear
------+---------------------------------
 2003 |                               1
 2003 |                               2
 2003 |                               1
 2002 |                               1
 2002 |                               1
 2002 |                               1
(6 rows)


uni_db=> SELECT extract(year from dob) AS Year,COUNT(*) AS no_of_students_BORN_IN_EACHYEAR
uni_db-> uni_db-> FROM students
uni_db->
uni_db-> SELECT extract(year from dob) AS Year,COUNT(*) AS no_of_students_BORN_IN_EACHYEAR
uni_db-> uni_db-> FROM students
uni_db-> uni_db-> GROUP BY dob;
ERROR:  syntax error at or near "uni_db"
LINE 2: uni_db-> FROM students
        ^
uni_db=> SELECT extract(year from dob) AS Year,COUNT(*) AS no_of_students_BORN_IN_EACHYEAR
uni_db-> uni_db-> FROM students
uni_db-> uni_db-> FROM students
uni_db->
uni_db-> ;
ERROR:  syntax error at or near "uni_db"
LINE 2: uni_db-> FROM students
        ^
uni_db=> SELECT extract(year from dob) AS Year,COUNT(*) AS no_of_students_BORN_IN_EACHYEAR
uni_db-> uni_db-> FROM students
uni_db-> ;
ERROR:  syntax error at or near "uni_db"
LINE 2: uni_db-> FROM students
        ^
uni_db=> DROP TABLE IF EXISTS students;
DROP TABLE
uni_db=> CREATE TABLE students(
uni_db(> student_id INTEGER,
uni_db(> first_name VARCHAR(50) NOT NULL,
uni_db(> last_name VARCHAR(50) NOT NULL,
uni_db(> email VARCHAR(100) UNIQUE,
uni_db(> dob DATE,
uni_db(> enrollment_status VARCHAR(10) CHECK (enrollment_status IN('enrolled','graduated','dropped')));
CREATE TABLE
uni_db=> INSERT INTO students(student_id,dob)
uni_db-> VALUES(1,'2003-09-15');
ERROR:  null value in column "first_name" of relation "students" violates not-null constraint
DETAIL:  Failing row contains (1, null, null, null, 2003-09-15, null).
uni_db=> DROP TABLE students;
DROP TABLE
uni_db=> CREATE TABLE students(
uni_db(> student_id SERIAL PRIMARY KEY,
uni_db(> first_name VARCHAR(50) NOT NULL,
uni_db(> last_name VARCHAR(50) NOT NULL,
uni_db(> email VARCHAR(50) UNIQUE,
uni_db(> dob DATE,
uni_db(> enrollment_status VARCHAR(20) CHECK(enrollment_status IN ('enrolled',graduated','dropped','pending')));
uni_db'>
uni_db'> ;
uni_db'> ;
uni_db'> \q

C:\Users\Minfy>psql -U uni_admin -d uni_db
Password for user uni_admin:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

uni_db=> CREATE TABLE students(
uni_db(> student_id SERIAL PRIMARY KEY,
uni_db(> first_name VARCHAR(50) NOT NULL,
uni_db(> last_name VARCHAR(50) NOT NULL,
uni_db(> email VARCHAR(50) UNIQUE,
uni_db(> dob DATE,
uni_db(> enrollment_status VARCHAR(20) CHECK(enrollment_status IN ('enrolled',graduated','dropped','pending'))
uni_db'> );
uni_db'> \q

C:\Users\Minfy>psql -U uni_admin -d uni_db
Password for user uni_admin:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

uni_db=> CREATE TABLE students (
uni_db(>     student_id SERIAL PRIMARY KEY,
uni_db(>     first_name VARCHAR(50) NOT NULL,
uni_db(>     last_name VARCHAR(50) NOT NULL,
uni_db(>     email VARCHAR(50) UNIQUE,
uni_db(>     dob DATE,
uni_db(>     enrollment_status VARCHAR(20) CHECK (enrollment_status IN ('enrolled', 'graduated', 'dropped', 'pending'))
uni_db(> );
CREATE TABLE
uni_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
uni_db-> VALUES ('Alice', 'Smith', 'alice.smith@example.com', '2003-05-15', 'enrolled');
INSERT 0 1
uni_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
uni_db-> VALUES ('Robert', 'Johnson', 'robert.j@example.com', '2002-08-22', 'enrolled');
INSERT 0 1
uni_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
uni_db-> VALUES ('Charlie', 'Brown', 'charlie.brown@example.com', '2003-01-10', 'pending');
INSERT 0 1
uni_db=> SELECT * FROM students;
 student_id | first_name | last_name |           email           |    dob     | enrollment_status
------------+------------+-----------+---------------------------+------------+-------------------
          1 | Alice      | Smith     | alice.smith@example.com   | 2003-05-15 | enrolled
          2 | Robert     | Johnson   | robert.j@example.com      | 2002-08-22 | enrolled
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-10 | pending
(3 rows)


uni_db=> CREATE TABLE courses(
uni_db(> course_id SERIAL PRIMARY KEY,
uni_db(> courses_name VARCHAR(20) NOT NULL UNIQUE,
uni_db(> credits INTEGER CHECK(credits > 0 AND credits < 10)
uni_db(> );
CREATE TABLE
uni_db=> INSERT INTO courses (course_name, credits) VALUES ('Introduction to SQL', 3);
ERROR:  column "course_name" of relation "courses" does not exist
LINE 1: INSERT INTO courses (course_name, credits) VALUES ('Introduc...
                             ^
uni_db=> INSERT INTO courses (course_name, credits) VALUES ('Database Design', 4);
ERROR:  column "course_name" of relation "courses" does not exist
LINE 1: INSERT INTO courses (course_name, credits) VALUES ('Database...
                             ^
uni_db=> INSERT INTO courses (course_name, credits) VALUES ('Web Development', 3);
ERROR:  column "course_name" of relation "courses" does not exist
LINE 1: INSERT INTO courses (course_name, credits) VALUES ('Web Deve...
                             ^
uni_db=> INSERT INTO courses (course_name, credits) VALUES ('Data Structures', 4);
ERROR:  column "course_name" of relation "courses" does not exist
LINE 1: INSERT INTO courses (course_name, credits) VALUES ('Data Str...
                             ^
uni_db=> INSERT INTO courses (course_name, credits) VALUES ('Data Structures', 4)
uni_db-> INSERT INTO courses (course_name, credits) VALUES ('Database Design', 4);
ERROR:  syntax error at or near "INSERT"
LINE 2: INSERT INTO courses (course_name, credits) VALUES ('Database...
        ^
uni_db=> INSERT INTO courses (course_name, credits) VALUES ('Introduction to SQL', 3);
ERROR:  column "course_name" of relation "courses" does not exist
LINE 1: INSERT INTO courses (course_name, credits) VALUES ('Introduc...
                             ^
uni_db=> INSERT INTO courses (courses_name, credits) VALUES ('Introduction to SQL', 3);
INSERT 0 1
uni_db=> INSERT INTO courses (courses_name, credits) VALUES ('Database Design', 4);
INSERT 0 1
uni_db=> INSERT INTO courses (courses_name, credits) VALUES ('Web Development', 3);
INSERT 0 1
uni_db=> CREATE TABLE enrollments (
uni_db(>     enrollment_id SERIAL PRIMARY KEY,
uni_db(>     student_id INTEGER NOT NULL,
uni_db(>     course_id INTEGER NOT NULL,
uni_db(>     enrollment_date DATE DEFAULT CURRENT_DATE, -- Sets default if not specified
uni_db(>     grade CHAR(1) CHECK (grade IN ('A', 'B', 'C', 'D', 'F', 'W', NULL)),
uni_db(> CONSTRAINT fk_student
uni_db(>    FOREIGN KEY(student_id)
uni_db(>    REFERENCES students(student_id)
uni_db(>    ON DELETE CASCADE,
uni_db(> CONSTRAINT fk_course
uni_db(>    FOREIGN KEY(course_id)
uni_db(>    REFERENCES courses(course_id)
uni_db(>    ON DELETE RESTRICT,
uni_db(> UNIQUE (student_id,course_id)
uni_db(> );
CREATE TABLE
uni_db=> INSERT INTO enrollments (student_id, course_id, grade) VALUES (1, 1, 'A');
INSERT 0 1
uni_db=> INSERT INTO enrollments (student_id, course_id) VALUES (1, 2); -- Grade will be NULL
INSERT 0 1
uni_db=> INSERT INTO enrollments (student_id, course_id, grade) VALUES (2, 1, 'B');
INSERT 0 1
uni_db=> SELECT * FROM enrollments;
 enrollment_id | student_id | course_id | enrollment_date | grade
---------------+------------+-----------+-----------------+-------
             1 |          1 |         1 | 2025-05-30      | A
             2 |          1 |         2 | 2025-05-30      |
             3 |          2 |         1 | 2025-05-30      | B
(3 rows)


uni_db=> SELECT * FROM students WHERE student_id = 1;
 student_id | first_name | last_name |          email          |    dob     | enrollment_status
------------+------------+-----------+-------------------------+------------+-------------------
          1 | Alice      | Smith     | alice.smith@example.com | 2003-05-15 | enrolled
(1 row)


uni_db=> SELECT * FROM enrollments WHERE student_id = 1;
 enrollment_id | student_id | course_id | enrollment_date | grade
---------------+------------+-----------+-----------------+-------
             1 |          1 |         1 | 2025-05-30      | A
             2 |          1 |         2 | 2025-05-30      |
(2 rows)


uni_db=> DELETE FROM students WHERE student_id = 1;
DELETE 1
uni_db=> SELECT * FROM students WHERE student_id = 1;
 student_id | first_name | last_name | email | dob | enrollment_status
------------+------------+-----------+-------+-----+-------------------
(0 rows)


uni_db=> SELECT * FROM enrollments WHERE student_id = 1;
 enrollment_id | student_id | course_id | enrollment_date | grade
---------------+------------+-----------+-----------------+-------
(0 rows)
