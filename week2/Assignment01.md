## Data Requirement
* readOnly fields are populated by application
  * timestamps
  * id
* writeOnly fields, values are provided by API caller in POST or PUT request, but not GET request. Not in response
* multipleOf keyword is used to specify that a number must be the multiple of another number.
* min and max are used to specify the range of possible values.

* All API req/res payloads should be in JSON
* proper HTTP status code
* using unit and/or integration tests
* only support **Token-Based** authen and not Session

---

ignore **account_created** and **account_updated** in **paylaods**
time stamps are set only when create or update is successful.
a user can only update their own account information.
user email already exist return **400**
store password using **BCrypt** with **Salt**
enforce strong password as recommened by **NIST**


## Schema
```
User{
    id	    
            string($uuid)
            example: d290f1ee-6c54-4b01-90e6-d701748f0851
            readOnly: true
    first_name*	    
            string
            example: Jane
    last_name*	
            string
            example: Doe
    password*	
            string($password)
            example: skdjfhskdfjhg
            writeOnly: true
    username*	// email adress
            string($email)
            example: jane.doe@example.com
    account_created	
            string($date-time)
            example: 2016-08-29T09:12:33.001Z
            readOnly: true
    account_updated	
            string($date-time)
            example: 2016-08-29T09:12:33.001Z
            readOnly: true
 
}
```

### Logic
#### service.js
```
async function authenticate({ username, password }) {
    const user = users.find(u => u.username === username && u.password === password);
    if (user) {
        const { password, ...userWithoutPassword } = user;
        return userWithoutPassword;
    }
}
```

#### controller.js
```
function authenticate(req, res, next) {
    userService.authenticate(req.body)
        .then(user => user ? res.json(user) : res.status(400).json({ message: 'Username or password is incorrect' }))
        .catch(err => next(err));
}
```

controller.authenticate(req.body) => service.authenticate({username, password}) => 
users.find({where: }) if(user) const {userWithoutPassword} return userWithoutPassword;
