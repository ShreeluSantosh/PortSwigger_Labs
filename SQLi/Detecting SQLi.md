# Detecting SQLi

## Systematic set of tests
- Single quote character `'`
- Boolean conditions like `OR 1=1` or `OR 1=2`
- SQL-specific syntax that evaluate to the base value of the entry point
- payloads that trigger time delays
- OAST payloads that trigger out-of-band network interaction
- Easier way: use Burp Scanner

## In different parts of the query
- most occur within `WHERE` clause of `SELECT` query
- also occur in:
  - In UPDATE statements, within the updated values or the `WHERE` clause.
  - `INSERT` statements, within the inserted values.
  - In `SELECT` statements, within the table or column name.
  - In `SELECT` statements, within the `ORDER BY` clause.

### Examples
- Retrieve hidden data: using `'--` to comment out the remaining part of SQL query, from URL
- Subvert app logic: using `--` to remove password check from app login page
- UNION attacks, to retrieve data from other databases:  `' UNION SELECT`
- Blind SQLi: app does not return the results of SQL query

### First order SQLi
App processes user input from HTTP request and incorporates input in SQL query, in an unsafe way
### Second order SQLi
App stores user input from HTTP request for future use. Later, the app retrieves the stored input and incorporates it in an unsafe way
Also known as stored SQLi
