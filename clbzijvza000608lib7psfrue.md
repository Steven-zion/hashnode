# Retrieve User Id from JWT Token

To get the user's ID from a JSON Web Token (JWT) stored in local storage in a React app, you can follow these steps:

1.  First, you will need to retrieve the JWT from local storage. You can do this using the `getItem` method of the `localStorage` object, like so:
    

```javascript
const jwt = localStorage.getItem('jwt');
```

2.  Next, you will need to decode the JWT to get the payload. The payload of a JWT is a JSON object that contains the claims (information about the user). You will need to decode the JWT to get the payload. The payload of a JWT is a JSON object that contains the claims. Claims are statements about an entity (typically, the user) and additional data. In this case, you are interested in the `sub` claim, which represents the subject of the JWT (i.e., the user's ID).To decode the JWT, you can use a library like `jwt-decode`.
    
    ```javascript
    //step 1
    import jwtDecode from 'jwt-decode';
    const decoded = jwtDecode(jwt);
    
    
    //alternative
    //or run 'npm install jsonwebtoken' then
    
    import jwt from 'jsonwebtoken';
    const payload = jwt.verify(jwt, 'your-secret-key');
    
    const userId = payload.sub;
    
    //Note that this process assumes that the JWT includes a sub claim with the user's ID. You will need to verify that this is the case, or modify the process accordingly if the JWT includes the user's ID in a different claim.
    ```
    
3.  The decoded object will contain the claims of the JWT, including the user's ID. You can access the ID like so:
    
    ```javascript
    const userId = decoded.userId;
    ```
    

Keep in mind that the structure of the decoded object will depend on how the JWT was created. The `userId` field may have a different name or be located at a different location in the object.

I hope this helps!