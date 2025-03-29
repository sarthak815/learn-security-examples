# Privilege Escalation

The example demonstrates a privilege escalation vulnerability and how to exploit it.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, send a GET request

    ```
        http://localhost:3000/send-form
    ```

4. Try different UserIds and see which one gives you authorized access to change the role of that user.

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
Ans: 
- There is no user authentication allowing unauthorized users to get access to sensitivie endpoints.
- The authorization check is solely based on the user's role in the the database which could have been manipulated
- The application allows direct modification of user roles.
2. Briefly explain how a malicious attacker can exploit them.
Ans: 
- The attacker can send a POST request to the /update-role endpoint with a valid userId and newRole bypassing any authentication.
- Attacker could impersonate the admin role and modify and manipulate roles for other users.
3. Briefly explain the defensive techniques used in **secure.ts** to prevent the privilege escalation vulnerability?
Ans:
 - Session based authentication to ensure that only logged-in users can access sensitive endpoints
 - Authorization checks are performed using session data to ensure only users with an admin role are allowed to update roles, ensuring that attackers can't bypass any authorization.
