# 20. Add Users to The MongoDB using Mongoose Model Schema and Check for Results

```
const user = new User({
    username: 'jack',
    password: '12345'
})

user.save((error) => {
    if (error) throw error;
    console.log("New user has been saved to the database successfully");
})
```