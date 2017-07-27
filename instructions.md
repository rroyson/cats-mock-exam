# Cats

## Objectives

- Update the api defined in this repo to send data back and forth to a mysql database as well as the existing

- Use environment variables to control:
  - The database platform (CouchDB or MySQL) the api "talks" to.
  - Manage connecting to mysql including ip address, database name, user name and password.


- Create the mysql database, tables, data and foreign key relationships.

- Create a script file to create the database, tables, foreign keys and data.  

- Provide developer documentation to minimize on-boarding friction including instructions on loading database setup script.  


## Getting Started

1. Fork the repo

  Sign in to your GitHub account and fork the following repo:

  ```
  https://github.com/jrs-innovation-center/cats-mock-exam
  ```

2. Clone your fork

  Clone your fork to your local machine and install the project's dependencies.

  ```
  $ git clone <url>
  $ cd cats-mock-exam
  $ yarn
  ```

## Steps

Successfully complete the first 4 steps to receive a grade of 'Meets Expectations'. Complete step 5 to receive a grade of 'Above Expectations'.

### Step 1

- Create a database, tables and data within a mysql database.  Include the following tables:

  - cat
  - breed

- Using a foreign key relationship, ensure each cat has a matching corresponding breed id.  Do not allow the deletion of a breed if the cat table contains corresponding record.

- Similar to previous **baseball.sql** example, create a **cats.sql** script file to create the database, tables, foreign keys and data.  Place the script within the **sql-scripts** folder.

### Step 2

- Use an environment variable to control which database platform (CouchDB or MySQL) the api "talks" to.  Provide the ability to switch database platforms when the api starts.  Ex:  `DAL=dal-sql node app.js`

- Use environment variables to manage connecting to mysql including ip address, database name, user name and password.

- Modify your `npm start` script to default to the sql dal.

### Step 3

Update the api defined in this repo to send data back and forth to a mysql database as well as the existing CouchDB database. Create a **dal-sql.js** file used to interact with a mysql database named **cats**.

- Ensure the api utilizes the same JSON schema for the mysql database as the CouchDB database.  Key names and data types within the JSON should remain the same.

- Ensure the following endpoints work for both a CouchDB and a MySQL database.  

  **CATS**

  - CREATE: `POST /cats`  
  - READ: `GET /cats/:id`  
  - UDPATE: `PUT /cats/:id`
  - DELETE: `DELETE /cats/:id`
  - LIST/FILTER/PAGINATE `GET /cats`

  **BREEDS**

  - CREATE: `POST /breeds`  
  - READ: `GET /breeds/:id`  
  - UDPATE: `PUT /breeds/:id`
  - DELETE: `DELETE /breeds/:id`

    >  Do not allow the deletion of a breed if the cat table contains corresponding record.  Send an 409 HTTP response with a message stating corresponding animal data exists for the breed you are attempting to delete.  Also include instructions on how to resolve the issue by removing all cats for the given breen.  A '409 Conflict' should be used when the request could not be completed due to a conflict with the current state of the resource. This code is only allowed in situations where it is expected that the user might be able to resolve the conflict and resubmit the request. The response body SHOULD include enough information for the user to recognize the source of the conflict. Ideally, the response entity would include enough information for the user or user agent to fix the problem.

    [https://http.cat/409](https://http.cat/409)
    [http://www.restapitutorial.com/httpstatuscodes.html](http://www.restapitutorial.com/httpstatuscodes.html)

  - LIST/FILTER/PAGINATE `GET /breeds`


### Step 4  - Getting Started

Modify existing developer on-boarding instructions by creating within your **README.md** file.  Be sure to provide developer documentation to minimize on-boarding friction including instructions on loading database setup script. Your IP address to your localhost will vary depending on whether you have a local install or using Docker.  

  Example (MySQL on Docker):

  ```
  cd sql-scripts
  $ mysql < baseball.sql -u root -p -h 0.0.0.0 -P 3306
  ```

### Step 5 - Reporting

Create a new endpoint `GET /breeds/reports/countweight`.

Return JSON to support the following report mock up. 

breed   | count |  avgWeight  |  maxWeight  | minWeight
--------|-------|---------------------------------------
tabby   |  2    |     10      |     12      |    8      
siamese |  3    |     12      |     14      |    10