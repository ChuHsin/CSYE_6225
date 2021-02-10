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
    username*	
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