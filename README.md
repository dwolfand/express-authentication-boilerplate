# Express Authentication Boilerplate
This is a simple authentication boilerplate made with NodeJS using Express and MongoDB. This application allows you to make a POST request to either a sign-in or sign-up endpoint allowing you to register, and re-auth with the service. Both endpoints return a JSON Web Token (JWT).

## Getting Started
This application can be installed via npm by running `npm install`. You'll need to also install MongoDB for the database hich will hold your users. With both installed run `mongod` first followed by `node index.js` to start the server. By default the server runs on port `3090`. 

If you get a permissions error related to the `/data/db` directory it may be neccersary to run the command listed [here](data/db/README.md).

For security purposes you'll also want to adjust the secret value found within `config.js`. Leaving it as its default value is highly unrecommended. 

## Endpoints
There's two POST endpoints that are provided.

### Signup
The  `/signup` endpoint expects a JSON object containing both an email address and password, once recieved it encrypts and stores the information in the database and returns a token. If you attempt to signup with an email that already exists in the database the server will reject it and return an error.


### Signin
The `/signin` endpoint also expects a JSON object containing both an email address and password, once recieved it checks if the user exists and if the provided password matches that of the one in the database. If it doesn't the server will reject the sign-in request and return an unauthorized error. If it does match the server will return a token.

Below is an example of the type of JSON object the endpoints expect.

```
{
"email": "example@example.com",
"password": "1323"
}
```