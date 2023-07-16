# Rest API Create using Nodejs and Json-server

## Technology and Tool Used
- Postman
- Node Js
- newman
- Json-Server
- npm
- Visual Studio Code

## Prerequisites

- You must have installed node js to your system
- Postman
- NPM
- Newman
- Json-Server

## Scenario of this project

- The user can create a user
- The user can create a user by id,name
- The user can get all users
- The user can get individual user by user id
- The user can update a user by user id
- The user can delete a user by user id

## API Documents

https://documenter.getpostman.com/view/16548351/2s946feCjX 


## How to create rest API using nodejs and json-server

Let’s start creating the REST APIs with our own data-

- First of all, ensure you have NodeJs and NPM installed.
- Create a folder name of your own choice on the desired location. For now, I have created with the name: Fake-APIs
- Run npm init inside the folder. It’ll prompt you with a set of questions and successfully create a package.json file. To avoid the set of questions, you can use npm init -y.
- Run npm install — save json-server. It’ll add the same dependency to the package.json file too. To install json-server globally, run npm install -g json-server. The folder structure looks as follows:


![image](https://github.com/Mamun104/restapi-create-nodejs-and-jsonserver/assets/78067017/2db1e40f-35ea-4df0-93aa-a0aefc267e71)

- We need to start our server now. To do so, open the package.json file and add a key-value in the scripts object after line 7: “json:server”:”json-server — watch users.json”.
- Open the command prompt and navigate to the folder. Run the command:
npm run json:server. It’ll run your server locally on http://localhost:3000

![image](https://github.com/Mamun104/restapi-create-nodejs-and-jsonserver/assets/78067017/25554f01-0ece-40f5-be2c-6742bd65e6f3)

- You should see a file named users.json created in the folder. When you run the server locally, it tries to search for the file (db.json) and if not found, it creates a file on its own with mock JSON data
- When you hit http://localhost:3000, you should see the following output. It has predefined 3 resources: posts, commands, profile. These resources are picked from the db.json file

![image](https://github.com/Mamun104/restapi-create-nodejs-and-jsonserver/assets/78067017/806cebc2-492a-4d16-95d6-f0fb122da5c0)

- Let’s go ahead and create a simple REST API that performs all CRUD operations-GET/POST/PUT/DELETE
- Refresh the browser window where your local server is running. You should see only one resource: users with a count of 3.
- Open Postman and make a GET request- http://localhost:3000/users. You should 3 users as a result.

  ![image](https://github.com/Mamun104/restapi-create-nodejs-and-jsonserver/assets/78067017/67bd9074-920a-4e52-8ce4-9a0be374d947)

## GET

- You can also perform operations such as sorting, filtering, searching, etc. Below are some of the examples:
* http://localhost:3000/users/2 (Returns the user with id-2)
* http://localhost:3000/users?_limit=2 (Sets the limit to return 2 records)
* http://localhost:3000/users?_sort=firstName&_order=desc (Sorts the records with the first name in descending order)
* http://localhost:3000/users?age_gte=40 (Returns the users whose age ≥40). Similarly you can set for age_lte and age_gte&age_lte
* http://localhost:3000/users?q=Sachin (Returns the users which contain the string “Sachin”)

## POST

- Let’s add one new user to the users request.
- Open a new tab in Postman and run the query (http://localhost:3000/users) with the POST operation. You need to set the header: Content-Type as application/json. In the body, select the body type as raw and add the following content:
{
“id”:4,
“firstName”:”Rohit”,
“lastName”:”Sharma”,
“age”:32
}

- If you make a GET call, you should see 4 users now.

## PUT
  
- Let’s modify the record with id 1
- Open a new tab in Postman and run the query (http://localhost:3000/users/1) with the PUT operation. You need to set the header: Content-Type as application/json. In the body, select the body type as raw and add the following content:
{
“firstName”:”Sachin”,
“middleName”:”Ramesh”,
“lastName”:”Tendulkar”,
“age”:47}

![image](https://github.com/Mamun104/restapi-create-nodejs-and-jsonserver/assets/78067017/43f34421-64d0-407b-a384-4575f67d79af)

- If you make a GET call, you should see that the first record is modified with the new result.

![image](https://github.com/Mamun104/restapi-create-nodejs-and-jsonserver/assets/78067017/d509e0f1-2d6d-479e-8ebf-79c613e486df)

## DELETE

- Let’s try to remove the user with id 3
- Open a new tab in Postman and run the query (http://localhost:3000/users/3) with the DELETE operation.
- The response is returned as empty {} object. This indicates that the object with the respective id is successfully deleted

- If you make a GET call, you should only see 3 users now.
