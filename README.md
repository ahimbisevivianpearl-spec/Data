# Data
constraints
A database table stores information in rows and columns.

For example, imagine a university keeping records of its students.
StudentID	StudentName	Course
101	John	BSIT
102	Mary	BLAW
103	Peter	BSIT

- Column: A type of information, such as StudentName.
- Row: One complete record about a student.
- Attribute: Another name for a column.
- Record/tuple: Another name for a row.
2. What is a primary key?
A primary key (PK) is a column, or combination of columns, that uniquely identifies every row in a table.

Look at our table:
StudentID (PK)	StudentName	Course
101	John	BSIT
102	Mary	BLAW
103	Peter	BSIT

StudentID is the primary key because every student has a different ID.

Notice that two students can study BSIT, so Course cannot uniquely identify each student.

A primary key must:
- Be unique.
- Never contain NULL values.
- Not repeat between rows.
3. What is a composite key?
Sometimes one column isn't enough to identify a record. We then combine two or more columns to form a composite key.

Imagine students registering for courses.
StudentID	CourseID	Grade
101	C01	A
101	C02	B
102	C01	A

Can StudentID alone be the primary key? No. Student 101 appears twice.

Can CourseID alone be the primary key? No. C01 appears twice.

But the combination of StudentID and CourseID is unique.

Therefore:
\[
\text{Primary Key}=(\text{StudentID},\text{CourseID})
\]

This is important because partial dependency in 2NF occurs when a non-key attribute depends on only part of a composite key.
4. The different types of keys
Key	Simple meaning
Primary key	Uniquely identifies a record.
Candidate key	A possible choice for the primary key.
Composite key	A key made of multiple columns.
Foreign key (FK)	Connects a table to another table.
Superkey	Any set of columns that uniquely identifies a record.


Your turn: Quick practice
1. Which column is the best primary key for a student table?

StudentName

StudentID

Course



2. A student can register for many courses. What key could identify each registration?

StudentID alone

CourseID alone

StudentID + CourseID



3. Which statement about a primary key is correct?

It can contain duplicate values

It can be NULL

It must uniquely identify each row


Try again
Once you understand these three questions, we'll move to Lesson 2: First Normal Form (1NF), where I'll show you how to identify an unnormalized table and correct it step by step.
















Done













Good! ❤️ Let's move to Lesson 2.
Lesson 2: First Normal Form (1NF)
First Normal Form (1NF) is the first stage of database normalization.

A table is in 1NF when:
1. Each cell contains only one value.
2. There are no repeating groups or lists of values in a cell.
3. Each row can be uniquely identified using a key.
Step 1: Identify the problem
Imagine a university has this table:
StudentID	StudentName	PhoneNumbers
101	John	070111, 075222
102	Mary	078333
103	Peter	070444, 077555

This table violates 1NF because John and Peter have multiple phone numbers stored in a single cell.
Step 2: Convert the table into 1NF
Separate the phone numbers so that each cell contains one value.
StudentID	StudentName	PhoneNumber
101	John	070111
101	John	075222
102	Mary	078333
103	Peter	070444
103	Peter	077555

Now each cell contains one value.

Important: If you use this table as written, StudentID alone is no longer unique. A possible primary key is (StudentID, PhoneNumber), assuming a student cannot have the same phone number recorded twice.
Step 3: How to answer an exam question
If an examiner gives you a table and asks you to convert it into 1NF:
- Identify cells containing multiple values.
- Separate those values into individual rows.
- Ensure each row can be uniquely identified.
- State that every attribute contains atomic values.
Remember: 1NF = one value per cell.

Your turn: Exam practice
QUESTION 1 · 2 MARKS

Consider this table:
StudentID	Name	Courses
01	Sarah	Database, Networking
02	David	Web Design

What is wrong with this table, and how would you correct it to achieve 1NF?

The table has no primary key. Add a new ID column.

Courses contains multiple values. Put each course in a separate row.

The names are too short. Add students' full names.

There are too few students. Add more rows.

Check answerCorrect! 🎉
Sarah's courses should be stored in separate rows, with one course per cell. This removes the repeating values and satisfies the atomic-value requirement of 1NF.

When you're ready, our next lesson is Second Normal Form (2NF). This is where composite keys and partial dependencies become important.
