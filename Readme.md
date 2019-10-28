$brew install node

$ vi server.js
~~~
var http = require('http');

var handleRequest = function(request, response) {
  console.log('Received request for URL: ' + request.url);
  response.writeHead(200);
  response.end('Hello World!!! v1.1');
};
var www = http.createServer(handleRequest);
www.listen(8082);
~~~

$ vi Dockerfile
~~~
 FROM node:6.9.2
 EXPOSE 8082
 COPY server.js .
 CMD node server.js
~~~

$ docker build -t hello-node:v1 .
