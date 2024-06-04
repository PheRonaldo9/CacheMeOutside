
---

# Students Database
This project includes a PostgreSQL script and two Bash scripts to manage and query data about computer science students in a PostgreSQL database.

---

# Student Information Management Scripts

This project includes a PostgreSQL script and two Bash scripts to manage and query data about computer science students in a PostgreSQL database. The scripts are designed to:
1. Set up the database and tables - SQL
2. Import student and course data from CSV files - Bash
3. Query specific information about students and courses from the database - Bash

## Prerequisites

Before running the scripts, ensure you have the following installed:

- PostgreSQL
- Bash

## Database Setup

First, set up the PostgreSQL database and tables using the provided SQL script - students.sql . This script will create the `students` database along with the necessary tables and constraints.

### Creating the Database

1. Save the provided SQL script to a file, e.g., `students.sql`.
2. Execute the script using the `psql` command:
   ```bash
   psql -U freecodecamp -f student.sql
   ```

This script will:

- Drop the existing `students` database if it exists.
- Create a new `students` database.
- Create the `courses`, `majors`, `majors_courses`, and `students` tables.
- Populate these tables with initial data.

## Importing Data

Use the provided Bash script - insert_data_bash_script to import data from the CSV files into the PostgreSQL database.

### Bash Script: `import.sh`

The Bash script reads data from `courses.csv` and `students.csv` and inserts it into the `students` database.

1. Save the provided Bash script to a file, e.g., `insert_data_bash_script.sh`.
2. Make the script executable:
   ```bash
   chmod +x insert_data_bash_script.sh
   ```
3. Run the script:
   ```bash
   ./insert_data_bash_script.sh
   ```

### CSV File Format

- `courses.csv` should contain two columns: `major` and `course`.
- `students.csv` should contain four columns: `first_name`, `last_name`, `major`, and `gpa`.

### Script Details

The script performs the following operations:

1. Truncates the existing tables (`students`, `majors`, `courses`, `majors_courses`).
2. Reads `courses.csv` and:
   - Inserts new majors and courses if they do not exist.
   - Associates majors with courses in the `majors_courses` table.
3. Reads `students.csv` and:
   - Inserts new students.
   - Associates students with their majors if the major exists.

## Querying Data

Use the provided Bash script to query specific information from the `students` database.

### Bash Script: `student_info.sh`

The Bash script queries the `students` database for specific information.

1. Save the provided Bash script to a file, e.g., `student_info.sh`.
2. Make the script executable:
   ```bash
   chmod +x student_info.sh
   ```
3. Run the script:
   ```bash
   ./student_info.sh
   ```

### Script Details

The script performs the following operations:

1. Retrieves the first name, last name, and GPA of students with a 4.0 GPA.
2. Lists all course names whose first letter is before 'D' in the alphabet.
3. Retrieves the first name, last name, and GPA of students whose last name begins with 'R' or later and have a GPA greater than 3.8 or less than 2.0.
4. Retrieves the last name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter.
5. Retrieves the first name, last name, and GPA of students who have not selected a major and either their first name begins with 'D' or they have a GPA greater than 3.0.
6. Lists the course names of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's'.
7. Calculates the average GPA of all students rounded to two decimal places.
8. Lists the major ID, total number of students in a column named 'number_of_students', and average GPA rounded to two decimal places in a column named 'average_gpa', for each major ID in the students table having a student count greater than 1.
9. Lists majors, in alphabetical order, that either no student is taking or has a student whose first name contains a case insensitive 'ma'.
10. Lists unique courses, in reverse alphabetical order, that no student or 'Obie Hilpert' is taking.
11. Lists courses, in alphabetical order, with only one student enrolled.

## Example Usage

1. Ensure PostgreSQL is running and the database is set up.
2. Prepare your CSV files (`courses.csv` and `students.csv`).
3. Execute the SQL script to set up the database.
4. Run the `insert_data_bash_script.sh` script to import the data.
5. Run the `student_info.sh` script to query specific information from the database.

---

## END

---

