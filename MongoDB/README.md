# MongoDB Readme

MongoDB Readme

#### MongoDB Connection 
```
// server.js (or your main application file)
const mongoose = require('mongoose');

// If you need to create connect with mongo Atlas or any other online mongo connecttion [Replace with your actual connection string] (common Templete)
// const mongoURI = 'mongodb+srv://<username>:<password>@<cluster.string>/<databaseName>?retryWrites=true&w=majority';

// If there is no username, password for local mongoDB 
const mongoURI = 'mongodb://localhost:27017/yourDatabaseName';

//Mongo with username , password
//const mongoURI = 'mongodb://username:password@localhost:27017/yourDatabaseName';

//You may also need to specify the authSource if your user credentials are in a different database than the one you are connecting to:
//const mongoURI = 'mongodb://username:password@localhost:27017/yourDatabaseName?authSource=admin'

/** If we had a replica set called repl1, consisting of three hosts, 192.168.10.1-3, and we were running them all on the default port, 27017, our connection string would look like this: **/
// const mongoURI = 'mongodb://192.168.1.1:27017,192.168.1.2:27017,192.168.1.3:27017/<database>?replicaSet=repl1'

mongoose.connect(mongoURI, {
  useNewUrlParser: true,
  useUnifiedTopology: true,
})
.then(() => console.log('MongoDB connected successfully!'))
.catch(err => console.error('MongoDB connection error:', err));

// Sample create record in mongo with schema
// Define a schema and model (example)
const userSchema = new mongoose.Schema({
  name: String,
  email: String,
});

const User = mongoose.model('User', userSchema);

// Example of using the model (e.g., to create a new user)
async function createUser() {
  try {
    const newUser = new User({ name: 'John Doe', email: 'john@example.com' });
    await newUser.save();
    console.log('User saved:', newUser);
  } catch (error) {
    console.error('Error saving user:', error);
  }
}

// Call the function to create a user (or perform other operations)
createUser();
```

