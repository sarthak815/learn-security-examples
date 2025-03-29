# Tampering

This example demonstrates tampering through script injection.

## Steps to reproduce

1. Install all dependencies

    `npm install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. In the browser, type a potentially malicious script in the name field of the form

    ```
        <script> document.body.innerHTML = "<a href='https://google.com'> Gotcha </a>"</script>
    ```

4. Do you see the potentially malicious hyperlink being injected into the form?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
Ans: In insecure.ts the inputs retrieved are not being sanitized. Due to this vulnerability the input is directly displayed on the front end.
2. Briefly explain how a malicious attacker can exploit them.
Ans: An attacker can pass a malicious script to the front end and this will be directly displayed. So an attacker could 
potentially pass a link which will now be displayed on the website's front end.
3. Briefly explain why **secure.ts** does not have the same vulnerabilties?
Ans. In secure.ts we sanitize the inputs obtained from the front end such that all escape tags in HTML are removed from the
text before being displayed in the front end. This ensures that only a string makes it through and not a script.
