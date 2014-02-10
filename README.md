# Install Node
Like JVM, since node is interpreted language, it need a interpreter, which is **node**. To download:

	sudo apt-get install nodejs

## Install Node through [Node Version Manager](https://github.com/creationix/nvm) (alternative)
	sudo apt-get install git
	sudo apt-get install curl
	curl https://raw.github.com/creationix/nvm/master/install.sh | sh
	nvm install 0.10
	nvm alias default 0.10
	
# Install Node Package Manager
Similar to [Composer](http://getcomposer.org/) for PHP, Node.js comes with a superior and dependable 
package management system called NPM and its registry **npmjs.org** which is easy to use and publish. 
Everything is administered via the **package.json** file and versioned locally, unless we’re installing 
a CLI tool with the _-g_ option. To Download npm:

	sudo apt-get install npm

## Install node module (pwd,no sudo) through npm
	npm search node-markdown
	npm install node-markdown
	npm install node-dev

# Development Flow with npm
Once npm is installed, the dev-flow will be:
* create *package.json* and define dependency modules
* install dependency modules
* update module if necessary
* write code
* test code
* publish module
* remove module	

## Create package.json
	npm init -- create default template
		dependencies {name:version}, * is the latest version
	npm install -- install all dependency modules
		install into prj/node_modules folder

## Run Application
	node your_app.js

## Update module
	cd prj; npm update
	[sudo] npm update -g  -- update all global module
		All global modules in /usr/local/libs/node_modules

## Remove module
	cd prj; npm prune

# Nodejs Framework (Middleware)
In the context of a web server, middleware is a layer between the guts
of the server and the code you’re writing to run on it that provides a set
of abstractions anyone writing code for the platform will be likely to
need. It differs from other modules you might pull into your application
in that it exists as a buffer between Node and your app, not a utility used
within your app.

## http

## connect
	$ npm install connect
### static module
	node_modules/connect/lib/middleware/static.js
	var connect = require("connect");
	connect(connect.static(__dirname + "/public")).listen(8000);
### router
	// create a router to handle application paths
	connect.router(function(app) {
		app.get("/sayHello/:firstName/:lastName", function(req, res) {
			var userName = req.params.firstName + " " + req.params.lastName,
			...

## querystring
Receiving data from query string.

	querystring = require("querystring");
	http.createServer(function(req, res) {
		// parse everything after the "?" into key/value pairs
		var qs = querystring.parse(req.url.split("?")[1]),
  		// property names are the same as in the querystring
  		userName = qs.firstName + " " + qs.lastName,
  		...
## url
Routing and receiving data from path

	// url like /sayHello/first name/last name:
 	var http = require("http"),
	url = require("url");
	http.createServer(function(req, res) {
	// split out parts of the path
	var path = url.parse(req.url).pathname.split("/");
	// handle GET requests to /sayHello/
	if (req.method == "GET" && path[1] == "sayHello") {
		var userName = path[2] + " " + path[3],
		...
 
* [Express.js](http://expressjs.com/) and EJS
  * Express provide a view system, which spit the output from template with customizable variables, it dependes on *connect*
  * Install Express and Generate Site with Express 
	* sudo npm install -g express@3.4.x
	* express recipes	
	* or express -e recipes -- which generate template with ejs support, default is jade	  
* [Meteor](https://www.meteor.com/)
* [Derby](http://derbyjs.com/)
* [Socket.io](http://socket.io/)

# Compare Nodejs and Browser
## Node Objects (Global)
	global
	require
	module
	process
	console

## Chrome Objects (Global)
	window
	location
	document
	console
	
# Module
The package.json file defines the dependency. Require will cache the loaded modules.
	require ('./a.js');	
	require ('./aFolder');
	require ('globalModule');
	
# Mocha for Unit Testing
	Test first (not always possible)
	Test afterwards
	npm install --save-dev mocha
	npm install --save-dev should
	npm install --save-dev supertest
	cd test; macha

# IDE (Eclipse) Setup
## [Nodeclipse] (http://www.nodeclipse.org/)
* install Eclipse [plugin](http://dl.bintray.com/nodeclipse/nodeclipse/0.8.0/)
* install command line tool

		sudo npm install -g nodeclipse
		nodeclipse -c projectName -u hello-world
		nodeclipse -p -- make pwd eclipse project
		
## [Emmet for Eclipse] (https://github.com/emmetio/emmet-eclipse)
* install [plugin](http://emmet.io/eclipse/updates/)
* customize the key (note: **Ctrl+D** conflicts with delete line)	

# Resource of Learning
## Javascript (and various associated framework) 
* [Code School](http://www.codeschool.com/) and [Codecademy](http://www.codecademy.com/) for the basics, with [NetTuts+](http://net.tutsplus.com/tutorials/javascript-ajax/javascript-objects/) being a good source for going into greater depth or viewing screencasts on more advanced topics and additional frameworks
* [Chrome Dev Tool tutorial video](http://discover-devtools.codeschool.com/chapters/5/challenges/5)
* [Node-tod at Github](https://github.com/scotch-io/node-todo)
* [Angular tutor in 30 minutes](http://www.revillweb.com/tutorials/angularjs-in-30-minutes-angularjs-tutorial/)
* [Angular Google CDN] (http://blog.angularjs.org/2012/07/angularjs-now-hosted-on-google-cdn.html)
* [Get Google CDN host your js library](http://encosia.com/3-reasons-why-you-should-let-google-host-jquery-for-you/)
* [The node beginner book](http://www.nodebeginner.org/)
 	
