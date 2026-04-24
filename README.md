# Student-Result-Management-System

A MySQL-based database project to manage student academic results,
calculate grades automatically, and generate performance reports
using advanced SQL concepts.

#Tech Stack

- Database: MySQL
- Concepts:DDL, DML, JOINs, Aggregate Functions, Views, Stored Procedures, CASE Statements, Normalization

#Features

- ✅ Add and manage Students, Subjects, and Marks
- ✅ Calculate total marks and percentage per student
- ✅ Auto grade classification (A+, A, B, C, D, Fail)
- ✅ Reusable SQL View for instant result reporting
- ✅ Stored Procedures for dynamic data operations
- ✅ Foreign key constraints for data integrity
- ✅ Identify failed students and top performers by department


#Database Schema

# students
| Column | Type | Description |
| student_id | INT (PK) | Auto-increment primary key |
| name | VARCHAR(100) | Student full name |
| email | VARCHAR(100) | Unique email address |
| department | VARCHAR(50) | Department name |
| year | INT | Current year of study |

# subjects
| Column | Type | Description |
| subject_id | INT (PK) | Auto-increment primary key |
| subject_name | VARCHAR(100) | Name of the subject |
| max_marks | INT | Maximum marks (default 100) |

# marks
| Column | Type | Description |
| mark_id | INT (PK) | Auto-increment primary key |
| student_id | INT (FK) | References students table |
| subject_id | INT (FK) | References subjects table |
| marks_obtained | INT | Marks scored by student |
| exam_date | DATE | Date of examination |


#Entity Relationship
students (student_id) ──< marks (student_id)
subjects (subject_id) ──< marks (subject_id)


#Stored Procedures

| Procedure | Parameters | Description |
|---|---|---|
| GetStudentReport | sid INT | Full subject-wise result for a student |
| GetFailedStudents | none | List all students with percentage < 50 |
| GetTopPerformer | dept VARCHAR | Top scorer in a given department |
| AddStudentMarks | s_id, sub_id, marks, date | Insert new marks record |

#Usage
CALL GetStudentReport(1);
CALL GetFailedStudents();
CALL GetTopPerformer('EEE');
CALL AddStudentMarks(2, 4, 78, '2024-11-13');

# SQL View

- student_report view gives instant result summary
SELECT * FROM student_report;
SELECT * FROM student_report WHERE grade = 'FAIL';
SELECT * FROM student_report ORDER BY percentage DESC;

# How to Run

1. Install MySQL and open MySQL Workbench
2. Open the `student_results.sql` file
3. Select all code and click Execute
4. All tables, data, views and procedures will be created automatically
5. Run queries or call procedures to test
   
