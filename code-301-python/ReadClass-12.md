# CRUD
#

In your own words, describe what each group of status code represents:
100’s —> The request is recieved and the rerver will try to complete the request.
200’s —> It means that the request is succesfully completed.
300’s —> It tells the client that the resource they are requesting isn’t available at the expected location anymore.
400’s —> Invalid requests
500’s —> Error from the server side.
#

What is a status code 202?
This code tells the client that the request was valid, but its processing will finish sometime in the future.
#

What is a status code 308?
This tells the client to use another URL to access the resource and not use the current URL anymore.
# -What code would you use if an update didn’t return data to a client?

204 or 404.
#

What code would you use if a resource used to exist but no longer does?
404
#

What is the ‘Forbidden’ status code?
4.3
# #

Why do we need to pull our MongoDB database string out of our server and put it into our .env?
To be hidden so that other people don’t use it and when deploying the service can change the path easy.
#

What is middleware?
Is software that lies between an operating system and the applications running on it. Essentially functioning as hidden translation layer, middleware enables communication and data management for distributed applications.
#

What does app.use(express.json()) do?
It parses incoming JSON requests and puts the parsed data in req.
#

What does the /:id mean in a route?
it’s a dynamic route, so req.params.id will be whatever comes after summary/ in that specific request.
#

What is the difference between PUT and PATCH?
PUT is a method of modifying resource where the client sends data that updates the entire resource . PATCH is a method of modifying resources where the client sends partial data that is to be updated without modifying the entire data.
#

How do you make a default value in a schema?
Your schemas can define default values for certain paths. If you create a new document without that path set, the default will kick in.
#

What does a 500 error status code mean?
Is a generic error response. It means that the server encountered an unexpected condition that prevented it from fulfilling the request.
#

What is the difference between a status 200 and a status 201?
The 200 status code is by far the most common returned. It means, simply, that the request was received and understood and is being processed. A 201 status code indicates that a request was successful and as a result, a resource has been created.
#