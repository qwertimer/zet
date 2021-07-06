# Learning Go [Part 4]

This zet outlines the development of the simple web server that i have developed using the go language. I have taken inspiration and development from:
 - whiteTulipGO https://thewhitetulip.gitbook.io/bo/,
 - rwxrob - go development,
 - Mat Ryer - https://www.youtube.com/watch?v=rWBSMsLG8po,
 - Tech with Tim - https://www.youtube.com/watch?v=75lJDVT1h0s&list=PLzMcBGfZo4-mtY_SE3HuzQJzuj4VlUG0q
 and others.

 The first step was to build a simple server using the http package. This is wrapped in a logger to catch any fatal issues. We can use log to time stamp to the terminal and indicate that the server has started by adding `log.Print` to the program.

The tutorial by whitetulip goes into depth on using databases for building a task app. Much of the tutorial is out of my current interest scope but what is of interest is some of the subsequent sections. 

Routing is used to route the server to the specific functions. We can use a useful package called `github.com/julienschmidt/httprouter` which is very powerful and provides routing for GET and POST and is advantageous in allowign the user to be more free with their URL order.

Middleware in webservers are essentially modular extensions to the website that doesn't know anything about the app but can provide additional functionality such as a login redirection middleware. 
