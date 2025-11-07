# PostgreSQL

PostgreSQL Queries

##### 1. Setup and Connection Pool:
First, install the pg package
```
npm install pg
```
Then, set up a connection pool to manage database connections efficiently:
```
const { Pool } = require('pg');

const pool = new Pool({
    user: 'your_username',
    host: 'localhost',
    database: 'your_database_name',
    password: 'your_password',
    port: 5432, // Default PostgreSQL port
});
```
##### 2. Executing a Simple SELECT Query:
```
async function getAllUsers() {
    try {
        const result = await pool.query('SELECT * FROM users');
        console.log('All users:', result.rows);
        return result.rows;
    } catch (err) {
        console.error('Error executing query', err.stack);
    }
}

getAllUsers();
```
##### 3. Executing a SELECT Query with Parameters:

This demonstrates how to use parameterized queries to prevent SQL injection.

```
async function getUserById(userId) {
    try {
        const result = await pool.query('SELECT * FROM users WHERE id = $1', [userId]);
        console.log('User by ID:', result.rows[0]);
        return result.rows[0];
    } catch (err) {
        console.error('Error executing query', err.stack);
    }
}

getUserById(1); // Assuming a user with ID 1 exists
```
##### 4. Executing an INSERT Query:

```
async function createUser(name, email) {
    try {
        const result = await pool.query(
            'INSERT INTO users (name, email) VALUES ($1, $2) RETURNING id',
            [name, email]
        );
        console.log('New user created with ID:', result.rows[0].id);
        return result.rows[0].id;
    } catch (err) {
        console.error('Error executing query', err.stack);
    }
}

createUser('John Doe', 'john.doe@example.com');
```

##### 5. Executing an UPDATE Query:

```
async function updateUserEmail(userId, newEmail) {
    try {
        await pool.query(
            'UPDATE users SET email = $1 WHERE id = $2',
            [newEmail, userId]
        );
        console.log('User email updated for ID:', userId);
    } catch (err) {
        console.error('Error executing query', err.stack);
    }
}

updateUserEmail(1, 'new.email@example.com');
```

##### 6. Executing a DELETE Query:

```
async function deleteUser(userId) {
    try {
        await pool.query('DELETE FROM users WHERE id = $1', [userId]);
        console.log('User deleted with ID:', userId);
    } catch (err) {
        console.error('Error executing query', err.stack);
    }
}

deleteUser(2); // Assuming a user with ID 2 exists
```

##### Important Notes:
- Error Handling: Always include try...catch blocks to handle potential errors during database operations.
- Connection Management: The Pool object automatically handles connection pooling, opening and closing connections as needed. You do not typically need to         - explicitly call client.end() when using a pool, as connections are returned to the pool for reuse.
SQL Injection: Always use parameterized queries ($1, $2, etc.) when incorporating user input into your SQL queries to prevent SQL injection vulnerabilities.

