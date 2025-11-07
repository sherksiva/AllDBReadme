# SQL Queries Docs

These are the fundamental operations you will perform:
##### SELECT: Retrieves data from one or more tables.

```
    SELECT column1, column2 FROM tableName WHERE condition;
```
##### INSERT INTO: Adds new rows of data to a table.

```
    INSERT INTO tableName (column1, column2) VALUES (value1, value2);
```
##### UPDATE: Modifies existing data in a table.

```
    UPDATE tableName SET column1 = newValue WHERE condition;
```
##### DELETE FROM: Removes rows from a table.
```
    DELETE FROM tableName WHERE condition;
```
#### Best Practices for Queries in Node.js:
Parameterized Queries: Use placeholders to prevent SQL injection vulnerabilities. This is crucial for security.
  ```
    connection.query('SELECT * FROM users WHERE id = ?', [userId], function (error, results, fields) {
        // handle results
    });
  ```
#### Asynchronous Handling (Promises/Async-Await): Leverage Node.js's asynchronous nature for non-blocking database operations.
```

    async function getUser(userId) {
        try {
            const [rows, fields] = await connection.execute('SELECT * FROM users WHERE id = ?', [userId]);
            return rows;
        } catch (error) {
            console.error('Error fetching user:', error);
            throw error;
        }
    }
```
- Error Handling: Implement robust error handling to gracefully manage database errors.
- Connection Pooling: Use a connection pool to efficiently manage database connections, reducing overhead.
- ORM/Query Builders (Optional but Recommended): Consider libraries like Sequelize, TypeORM, or Knex.js for a more abstract and structured way to interact with       your database, offering features like schema migrations, model definitions, and easier query building.
#### Query Optimization:
- Use Indexes: Improve query performance, especially on frequently queried columns.
- Avoid SELECT *: Only select the columns you need.
- Optimize JOIN clauses: Ensure efficient joining of tables.
Limit Result Sets: Use LIMIT to retrieve only necessary data.

