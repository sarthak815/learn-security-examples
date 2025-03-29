# Repudiation

The example demonstrates a vulnerability that can lead to repudiation by malicious users attempting to access the services provided by a server.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Run the server __insecure.ts__.

3. Pretend to be a malicous user and interact with the services by sending requests from the browser.

4. Do you think your actions can be repudiated?

## For you to do

1. Briefly explain the vulnerability.
Ans: When a message is sent there is no log of who sent a message and when they might have sent it. Due to this someone can
always deny accountability for their actions by blaming it as a software error. Similarly on other endpoints as well someone could deny their actions and the application would be accountable for erroneous actions.
2. Briefly explain why the vulnerability is addressed in __secure.ts__.
Ans: In secure.ts at all major endpoints the action is logged. Such as when a message is sent the application logs who sent the message and what the message sent here was.
3. Which design pattern is used in the secure version to address the vulnerability? Briefly explain how it works?
Ans: The application uses chain of responsibility design pattern by defining a middleware to handle logging. The loggging middleware logs details of the request and metadata of every incoming request before passing control to the next middleware or route handler. After moving through the chain and reaching the route handler more specific details to the endpoint called are logged.
