---
layout: post
section-type: post
title:  "Running parse5 in Linux Mint"
category: HTML5
comments: true
tags: [ 'tutorial' ]
---

This walkthrough is to install and run parse5 in **Linux Mint**, 64 bits architecture.

## What is parse5

**parse5** is a HTML5 parser build in javascript for *Node.js* or *io.js*. This is a implementation of the WHATWG specification. 
The current version is the 4.0.0 and it seems that is currently maintained according to their repository activity.

There are others Html parsers ( [htmlparser2](https://www.npmjs.com/package/htmlparser2),[html5](https://www.npmjs.com/package/html5) ) but I chose this one because it specifies that is
WHATWG html specification compliant, is the one that shows to be alive (github files were updated recently) and because it was tested against the [HTML5Lib tests](https://github.com/html5lib/html5lib-tests)

For more info follow the following links:

[https://github.com/inikulin/parse5](https://github.com/inikulin/parse5)

[https://www.npmjs.com/package/parse5](https://www.npmjs.com/package/parse5)

**parse5** is a software for Node.js or io.js. In this walkthrough, I will use **Node.js**[^node] which includes **npm**[^npm] a package manager for javascript. This package manager will help us
to download and install parse5 and its dependencies.

### Download and install node.js

Download Node.js from their website [https://nodejs.org/download/](https://nodejs.org/download/)

Install the dependencies. If you don't do this you are probably get an error like `make[1]: g++: Command not found`
	
{% highlight sh %}
sudo apt-get install g++ curl libssl-dev apache2-utils
sudo apt-get install git-core
{% endhighlight %}

If you don't do this you are probably get an error like make[1]: g++: Command not found

Then build:

{% highlight sh %}
./configure
make
sudo make install
{% endhighlight %}

To test is working, do the sever example of the [node website](https://nodejs.org) :

Write in a example.js file: 

{% highlight js %}
var http = require('http');
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World\n');
}).listen(1337, '127.0.0.1');
console.log('Server running at http://127.0.0.1:1337/');
{% endhighlight %}

{% highlight sh %}
$ node example.js
Server running at http://127.0.0.1:1337/
{% endhighlight %}

Once node.js is installed we should have npm installed as well. Lets check version:

{% highlight sh %}
$ npm -version
2.10.1
{% endhighlight %}

## Download and install parse5

Now let npm do this job:

{% highlight sh %}
$ npm install parse5
{% endhighlight %}

To test it is working lets run the following example, just create a file **example.js** and copy the code below:

{% highlight js %}
var Parser = require('parse5').Parser;

//Instantiate parser
var parser = new Parser();

//Then feed it with an HTML document
var document = parser.parse('Hello!')

var parse5 =  require('parse5');

//Instantiate new serializer with default tree adapter
var serializer1 = new parse5.Serializer();

//Serialize document
var output = serializer1.serialize(document);

//Show the serialized DOM
console.log(output);
{% endhighlight %}

And run it:

{% highlight sh %}
$ node example.js 
<html><head></head><body>Hello!</body></html>
{% endhighlight %}

As you can see, the malformed html input `Hello!` was parsed and a correct DOM generated.

## Running the html5lib tests

In order to run the html5lib tests, download the source code and test files from their github [repository](https://github.com/inikulin/parse5). 
Lets download the zip and decompress the content. 

I got a dependency error when i tried to run the tests:

{% highlight sh %}
module.js:338
    throw err;
          ^
Error: Cannot find module 'mocha'
    at Function.Module._resolveFilename (module.js:336:15)
    at Function.Module._load (module.js:278:25)
    at Module.require (module.js:365:17)
    at require (module.js:384:17)
{% endhighlight %}

To fix this, install this module with `npm install mocha`. This module is actually the test framework that help running the tests.

After that run the tests:

{% highlight sh %}
$ npm test

> parse5@1.4.2 test /home/jose/HTML5Parsers/parser5_js/parse5-master
> node test/run_tests.js


  [▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬]
  
  12606 passing (7s)
{% endhighlight %}




[^npm]:[https://www.npmjs.com/](https://www.npmjs.com/)
[^node]:[https://nodejs.org](https://nodejs.org)