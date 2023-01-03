BUG 1 - The GET route to /users. In our route, we are looking to get *basic* in formation. However our function getAll() returned all user info including phone & email address. Fixed the bug by altering the SQL query in our model.

BUG 2 - The GET route to /users/username. Function get(username) should output a 404 response when username cannot be found. Fixed this by throwing the ExpressError in our model if user is not found.

BUG 3 - The POST route to /auth/login does not return 401 error if bad username/password combo.

BUG 4 - POST route to /auth/login did not contain "await", this lead to our app generating a JWT for any username/password combo.

BUG 5 - Middlware -> authUser is accepting the token, and decoding it but is not VERIFYING that the token is valid (signed from our server) therefore any bad actor can generate a JWT with username & admin set to     TRUE and wreak havoc on our DB.

BUG 6 - PATCH route, this route was using middleware for ensuring admin user. Preventing current logged in user from editing their own info.