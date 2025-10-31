# MongoDB Readme

MongoDB Readme

#### MongoDB Connection 
```
// server.js (or your main application file)
const mongoose = require('mongoose');

// Replace with your actual connection string
const mongoURI = 'mongodb+srv://<username>:<password>@<cluster.string>/<databaseName>?retryWrites=true&w=majority'; 

mongoose.connect(mongoURI, {
  useNewUrlParser: true,
  useUnifiedTopology: true,
})
.then(() => console.log('MongoDB connected successfully!'))
.catch(err => console.error('MongoDB connection error:', err));

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

