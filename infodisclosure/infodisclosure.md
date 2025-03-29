# Tampering

This example demonstrates information disclosure by injecting malicious query objects to a NoSQL database.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Insert test data in the MongoDB database. Make sure the mongod is up and running by typing the `mongosh` command in the termainal. If mongod process is up then you will see that the connection was successful. Command to insert test data:

    `$ npx ts-node insert-test-users.ts`

This will create a database in MongoDB called __infodisclosure__. Verify its presence by connecting with mongosh and running the command `show dbs;`.

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, pretend to be a hacker and type a malicious request

    ```
        http://localhost:3000/userinfo?username[$ne]=
    ```

4. Do you see user information being displayed despite the malicious request not having a valid username in the request?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
Ans: The user directly uses the user-supplied input in the MongoDB query without validation or sanitization. 
2. Briefly explain how a malicious attacker can exploit them.
Ans: This allows any user to pass MongoDB queries as input and access confidential information or even write erroneous values. If an attacker passed 'ne' on an empty string as a Mongo query instead of an username the attacker would be able to see all the values in the database.
3. Briefly explain the defensive techniques used in **secure.ts** to prevent the information disclosure vulnerability?
Ans: In secure.ts the application performs input validation by removing all alphanumeric values. This prevents a NOSQL injection by ensuring that special characters cannot be passed as inputs. Also errors in the database queries are caught and logged and a generic error message is passed to the client. This prevents attackers from gaining insights into internal application details.
