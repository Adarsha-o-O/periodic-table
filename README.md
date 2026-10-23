# Periodic Table Database

A command-line periodic table lookup project built with **Bash and PostgreSQL** as part of the freeCodeCamp Relational Database curriculum.

The project stores chemical element information in a relational database and retrieves an element's properties using its atomic number, chemical symbol, or name.

## Features

- Search for an element by atomic number, symbol, or name.
- Retrieve element properties using SQL queries.
- Join related tables to combine element details, physical properties, and classification.
- Display atomic mass, melting point, boiling point, and element type.
- Handle missing input and elements that are not found in the database.

## Technologies

- **Bash** — command-line input and application logic.
- **PostgreSQL** — relational database management.
- **SQL** — queries, joins, constraints, and relational data organization.
- **psql** — PostgreSQL command-line interface.

## Project Structure

```text
periodic-table/
├── element.sh
├── periodic_table.sql
└── README.md
```

| File | Description |
|---|---|
| `element.sh` | Accepts an element identifier, queries the database, and displays the result. |
| `periodic_table.sql` | Database dump containing the schema, constraints, and data. |
| `README.md` | Project documentation. |

## Database Schema

The database uses three related tables:

- **`elements`** — stores atomic number, chemical symbol, and element name.
- **`properties`** — stores atomic mass, melting point, boiling point, and a reference to the element type.
- **`types`** — stores element classifications such as nonmetal, metal, and metalloid.

The schema uses primary keys, unique constraints, and foreign keys to maintain relationships between records.

The supplied database contains information for the first ten elements of the periodic table.

## Prerequisites

- PostgreSQL
- `psql` command-line client
- Bash-compatible shell

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/Adarsha-o-O/periodic-table.git
cd periodic-table
```

### 2. Set up PostgreSQL

The supplied `periodic_table.sql` dump recreates a database named `periodic_table` and assigns ownership to the `freecodecamp` role.

**Warning:** The dump contains `DROP DATABASE periodic_table;`. Review the file before running it because importing it can delete an existing database with that name.

Restore the database in a suitable PostgreSQL environment with the necessary privileges. For example:

```bash
psql -U postgres -d postgres -f periodic_table.sql
```

The PostgreSQL role and ownership settings may need adjustment for your local installation.

### 3. Configure database access

The script connects using the following settings:

```bash
psql --username=freecodecamp --dbname=periodic_table
```

Make sure the `freecodecamp` role exists and has the required database permissions, or modify `element.sh` to match your local PostgreSQL configuration.

### 4. Run the script

On Linux or a Bash-compatible environment, make the script executable:

```bash
chmod +x element.sh
```

Then search for an element.

**By atomic number:**

```bash
./element.sh 1
```

**By symbol:**

```bash
./element.sh He
```

**By name:**

```bash
./element.sh Carbon
```

## Example Output

For Hydrogen, the script produces output in this format:

```text
The element with atomic number 1 is Hydrogen (H). It's a nonmetal, with a mass of 1.008 amu. Hydrogen has a melting point of -259.1 celsius and a boiling point of -252.9 celsius.
```

## What I Practiced

This project provided practical experience with:

- Designing and querying a relational database.
- Connecting Bash scripts to PostgreSQL.
- Retrieving data using SQL `SELECT` statements.
- Joining multiple tables using `JOIN`.
- Using primary keys, unique constraints, and foreign keys.
- Passing command-line arguments to a shell script.
- Handling missing input and unsuccessful database lookups.

## Current Scope

This repository contains the database and command-line lookup implementation developed during the learning project. It currently includes data for ten chemical elements and does not represent a complete periodic table database.

## Learning Context

Created as part of the **freeCodeCamp Relational Database curriculum**.

- GitHub repository: [periodic-table](https://github.com/Adarsha-o-O/periodic-table)
- Developer: [Adarsha-o-O](https://github.com/Adarsha-o-O)

