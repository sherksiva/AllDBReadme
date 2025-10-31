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
