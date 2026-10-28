# SQL Important Docs

SQL Readme
```
    const mysql = require('mysql');

    const dbConfig = {
        host: 'localhost',
        user: 'your_username',
        password: 'your_password',
        database: 'your_database_name'
    };

    const connection = mysql.createConnection(dbConfig);

    connection.connect((err) => {
        if (err) {
            console.error('Error connecting to database:', err.stack);
            return;
        }
        console.log('Connected to MySQL database with ID:', connection.threadId);
    });
```
#### Find Duplicate Records 

```
SELECT Name, Department, COUNT(*) AS DuplicateCount
FROM Employees
GROUP BY Name, Department
HAVING COUNT(*) > 1;
```

```
SELECT Email, COUNT(*) AS DuplicateCount
FROM Employees
GROUP BY Email
HAVING COUNT(*) > 1;
```
```
SELECT email, COUNT(*) as occurrences
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

