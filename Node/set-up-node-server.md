# Set Up a Node Server

```
var http = require('http');

var server = http.createServer(function(request, response){
	console.log('Got a request!');
	response.write('hi!');
	response.end();
});

server.listen(3002);
```