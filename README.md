# Students-Database
Bash script that uses SQL to enter information about your computer science students into PostgreSQL

---

# Student Information Import Script

This project includes a Bash script to import data about computer science students into a PostgreSQL database. The script reads data from two CSV files (`courses.csv` and `students.csv`) and inserts the data into the appropriate tables in the `students` database.

## Prerequisites

Before running the script, ensure you have the following installed:

- PostgreSQL
- Bash

## Database Setup

First, set up the PostgreSQL database and tables using the provided SQL script. This script will create the `students` database along with the necessary tables and constraints.

### Creating the Database

1. Save the provided SQL script to a file, e.g., `setup.sql`.
2. Execute the script using the `psql` command:
   ```bash
   psql -U freecodecamp -f setup.sql
   ```

This script will:

- Drop the existing `students` database if it exists.
- Create a new `students` database.
- Create the `courses`, `majors`, `majors_courses`, and `students` tables.
- Populate these tables with initial data.

## Importing Data

Use the provided Bash script to import data from the CSV files into the PostgreSQL database.

### Bash Script

The Bash script reads data from `courses.csv` and `students.csv` and inserts it into the `students` database.

1. Save the provided Bash script to a file, e.g., `import.sh`.
2. Make the script executable:
   ```bash
   chmod +x import.sh
   ```
3. Run the script:
   ```bash
   ./import.sh
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

## Example Usage

1. Ensure PostgreSQL is running and the database is set up.
2. Prepare your CSV files (`courses.csv` and `students.csv`).
3. Execute the SQL script to set up the database.
4. Run the Bash script to import the data.

---

## END
