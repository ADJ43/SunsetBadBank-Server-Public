# SunsetBadBank-Server

# Andres Jose Sunset BadBank Application API Documentation

NodeJS Server for SunsetBadBankApp

A summary of the API functionality:

The API was built using NODE JS and ExpressJS. It is a small and easy to use API that allows you to interact with the database and the server.
This are the dependencies that are used:


### Dependencies
    "cors": "^2.8.5",
    "dotenv": "^16.0.1",
    "express": "^4.18.1",
    "mongodb": "^4.8.0"


### Deployment

This API is deployed on Heroku. Some of the code has been modified to make it work with the heroku. (e.g. the port number, Procfile, etc.)

### Main Files

There are three main files that comprise the API:
    - index.js: This is the main file that runs the server.
    - routes/record.js: This file contains the routes for the API.
    - db/conn.js: This file contains the connection to the database.


### API Endpoints

    - /:email This endpoint deletes the record that matches the email provided. DELETE method has to be used.
    - /record This endpoint returns all the records in the database. GET method has to be used.
    - /record/:email This endpoint returns the record that matches the email provided. GET method has to be used.
    - /update/:email This endpoint updates the record that matches the email provided. POST method has to be used.
    - /record/add This endpoint adds a new record to the database. POST method has to be used.


### Notes on /UPDATE/ and RECORD/ADD/ Endpoints

In this 2 cases, the email is the key that is used to identify the record.
You will also need to provide additional information to update the record or add a new one.

### Notes on /RECORD/ADD Endpoint
recordRoutes.route("/record/add").post(function (req, response) {
 let db_connect = dbo.getDb();
# let myobj = {
#   email: req.body.email,
#   accountNumber: req.body.accountNumber,
#   routingNumber: req.body.routingNumber,
#   balance: req.body.balance,
 };
 db_connect.collection("records").insertOne(myobj, function (err, res) {
   if (err) throw err;
   response.json(res);
 });
});

### Notes on UPDATE Endpoint

recordRoutes.route("/update/:email").post(function (req, response) {
 let db_connect = dbo.getDb(); 
 let myquery = {email:( req.params.email )}; 
 let newvalues = {   
#   $set: {     
#      // email: req.body.email, (Commented, not in use)
#      // accountNumber: req.body.accountNumber,  (Commented, not in use)
#      // routingNumber: req.body.routingNumber,  (Commented, not in use)
#     balance: req.body.balance,  
   }, 
  };
  db_connect.collection("records").updateOne(myquery, newvalues, function (err, res) {
    if (err) throw err;
    console.log("1 document updated");
    response.json(res);
  });
});


### Examples of API Endpoints in the browser

    - http://localhost:3000/record                          - Returns all the records in the database.
    - http://localhost:3000/record/add                      - Adds a new record to the database.
    - http://localhost:3000/                                - Deletes a record that matches the email provided.
    - http://localhost:3000/update/example@example.com      - Updates the record that matches the email provided.
    - http://localhost:3000/record/example@example.com      - Returns the record that matches the email provided.



### Developer Guide

Developers will be able to make use of the API by using the following endpoints:
    - /record                                               - Returns all the records in the database.
    - /record/add                                           - Adds a new record to the database.
    - /                                                    - Deletes a record that matches the email provided.
    - /update/:email                                       - Updates the record that matches the email provided.
    - /record/:email                                       - Returns the record that matches the email provided.

It is also possible to modify, add or remove features, the API is very flexible and can be used to add new features to the application.


### API RESPOSES

    - 200: Successful request.
    - 400: Bad request.
    - 404: Not found.
    - 500: Internal server error.


### API REQUESTS

All the GET requests are used to retrieve data from the database. This will return a JSON object with the data.
POST and DELETE requests also return data of the same type, if the request is successful.



### This API Documentation was created by Andres Jose.
### It will be updated regularly.

[]: # Language: markdown
[]: # Path: README.md
