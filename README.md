# 1. What is CORS?
CORS stands for Cross-Origin Resource Sharing. It's a mechanism that allows web applications to make requests to resources located on a different domain than the one where the application is running. This is important because for security reasons, **browsers have a built-in same-origin policy** that restricts what resources a web application can access.
## Why is it needed?
 - Websites and web applications often rely on resources from different domains, such as third-party APIs, fonts, or data feeds.
 - Without CORS, these resources wouldn't be accessible due to the same-origin policy.
## Where do we define cors configuration?
you'll need to configure it on the server that's receiving the cross-origin requests, not on the client-side where the requests originate.
## What is preflight request?
In simple terms, a preflight request is like asking for permission before actually making a certain type of request to a web server. It's part of a security mechanism used by web browsers to check if it's okay to send a particular type of request (such as POST or PUT) to a different domain than the one that served the web page.

Let's say you have a web page on domain "example.com," and your JavaScript code in that page wants to make a POST request to a different domain, let's call it "api-server.com." Before the actual POST request, the browser sends a preflight request to "api-server.com" to check if it's allowed.

Preflight Request:

Browser: "Hey, api-server.com, I'm about to make a POST request with some specific headers and methods. Is it cool?"
Preflight Response:

Server (api-server.com): "Yes, example.com, you are allowed to make a POST request with those headers and methods."
Actual Request (if preflight is successful):

Browser: "Great! Now, here's the actual POST request with the data."
This process helps ensure that only allowed requests are made, preventing potential security issues. It's like checking with the server if it's okay to proceed before actually sending sensitive information or making certain types of requests.

## Does preflight cause latency in the application?
Preflight requests can introduce some latency to the overall process of making cross-origin requests. This is because it involves an additional round-trip to the server before the actual request can be sent.
To mitigate the impact on performance, developers can use techniques such as caching preflight responses or configuring servers to explicitly allow certain types of cross-origin requests without the need for a preflight check, depending on the security requirements of the application
