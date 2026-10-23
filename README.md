# Periodic Table Database

A Bash and PostgreSQL project completed as part of freeCodeCamp's **Relational Databases Certification**, under the *Build a Periodic Table Database* challenge.

The project uses a relational database to store chemical element information and a Bash script to retrieve and display details about an element based on its atomic number, symbol, or name.

## Features

- Search for an element by atomic number, chemical symbol, or element name.
- Retrieve the element's atomic number, symbol, name, atomic mass, melting point, and boiling point.
- Classify elements by type using a relational database.
- Combine information from multiple tables using SQL joins.
- Handle missing command-line arguments and elements that are not found.
- Query PostgreSQL from a Bash script using `psql`.

## Technologies Used

- **Bash** — command-line scripting
- **PostgreSQL** — relational database management
- **SQL** — database queries, table definitions, and constraints
- **psql** — PostgreSQL command-line client

## Repository Structure

```text
periodic-table/
├── element.sh
├── periodic_table.sql
└── README.md
```

| File | Description |
|---|---|
| `element.sh` | Accepts an element identifier and queries the database. |
| `periodic_table.sql` | SQL dump containing the database schema and element data. |
| `README.md` | Project documentation and setup instructions. |

## Database Design

The database contains three related tables:

- **`elements`** — stores each element's atomic number, symbol, and name.
- **`properties`** — stores atomic mass, melting point, boiling point, and the element's type ID.
- **`types`** — stores the classification of each element, such as metal, nonmetal, or metalloid.

Primary keys, unique constraints, and foreign keys help maintain relationships and data integrity.

The current database contains the first ten elements of the periodic table, from Hydrogen to Neon.

## How It Works

1. The user provides an atomic number, symbol, or element name as a command-line argument.
2. The Bash script executes a PostgreSQL query through `psql`.
3. SQL joins retrieve the element's properties and classification.
4. The script displays the matching element's information or an appropriate message if the input is missing or no match is found.

## Setup and Usage

### Prerequisites

- Bash shell
- PostgreSQL
- PostgreSQL command-line client (`psql`)
- A configured PostgreSQL role with access to the `periodic_table` database

### 1. Clone the repository

```bash
git clone https://github.com/Adarsha-o-O/periodic-table.git
cd periodic-table
```

### 2. Restore the database

The `periodic_table.sql` file is a database dump. Before restoring it, inspect the file: **it contains commands to drop and recreate the `periodic_table` database**, which may delete an existing database with that name.

To restore the dump using a PostgreSQL administrator role, run:

```bash
psql -U postgres -d postgres -f periodic_table.sql
```

The role and permissions required to execute the dump may vary depending on your PostgreSQL setup.

### 3. Configure database access

The script connects using the following database settings:

```bash
psql --username=freecodecamp --dbname=periodic_table
```

Ensure that the PostgreSQL role `freecodecamp` exists and has the necessary permissions to connect to the database and read its tables. If your local configuration differs, update the connection settings in `element.sh`.

### 4. Make the script executable

On Linux or another compatible Bash environment, run:

```bash
chmod +x element.sh
```

### 5. Search for an element

Search by atomic number:

```bash
./element.sh 1
```

Search by symbol:

```bash
./element.sh He
```

Search by element name:

```bash
./element.sh Carbon
```

The script displays the matching element's information. If no argument is supplied or the element cannot be found, it displays a corresponding message.

## Example Output

Illustrative output for Hydrogen:

```text
The element with atomic number 1 is Hydrogen (H).
It's a nonmetal, with a mass of 1.008 amu.
Hydrogen's melting point is -259.1 celsius.
Hydrogen's boiling point is -252.9 celsius.
```

Actual output depends on the script and the values stored in the database.

## What I Learned

By completing this project, I gained practical experience with:

- Designing a relational database with multiple related tables.
- Creating primary keys, unique constraints, and foreign keys.
- Writing SQL queries using `SELECT`, `WHERE`, and `JOIN`.
- Retrieving database records from a Bash script.
- Handling command-line arguments.
- Using PostgreSQL's `psql` command-line client.
- Exporting a database to an SQL dump for project submission.

## Learning Context

This project was completed as part of the **freeCodeCamp Relational Databases Certification**.

Challenge: [Build a Periodic Table Database](https://www.freecodecamp.org/learn/relational-databases/)

## Future Improvements

- Expand the database to include all chemical elements.
- Use safer parameter handling to avoid inserting raw user input directly into SQL queries.
- Improve database connection configuration.
- Add automated tests for different search inputs and error cases.

---

**Author:** [Adarsha-o-O](https://github.com/Adarsha-o-O)

