exceptional
===========

Fantastic error messages for Node. This module is still very experimental and you might experience great frustration if the exceptional error handler fails. You'll have to debug exceptional itself in that case...

Example
=======

The output is colored too. I'll embed an image here sometime but here's what it looks like uncolored:

```
ReferenceError: nonexistentFunc is not defined
/Users/abi/stuff/repos/node/exceptional/examples/example.js
	2: (function() {
	3:   var a;
	4:   require('../lib/exceptional');
	5:  >a = 5;
	6:   nonexistentFunc();
	7:   a();
	8: }).call(this);
/Users/abi/stuff/repos/node/exceptional/examples/example.js
	3:   var a;
	4:   require('../lib/exceptional');
	5:   a = 5;
	6:   nonexistentFunc();
	7:   >();
	8: }).call(this);
Module._compile (module.js:402:26)
Object..js (module.js:408:10)
Module.load (module.js:334:31)
Function._load (module.js:293:12)
Array.<anonymous> (module.js:421:10)
EventEmitter._tickCallback (node.js:126:26)
```

Usage
=====

`npm install exceptional`

And in your node module that you are debugging,

`require 'exceptional'`

Notes about Coffee use
======================

Using this directly with the Coffee executable is a bad idea because this depends on the node process emitting the uncaughtException which happens to be handled by the Coffee executable directly. See this [Stack Overflow question](http://stackoverflow.com/questions/6346291/nodejs-and-coffeescript-coffee-executable-not-behaving-the-same/6350100#6350100) for details. You can of course do this instead,

`coffee -c x.coffee && node x.js`

This is what I do currently.

TODO
====

* Re-write all code (it's really ugly right now)
* Figure out a better color scheme
* Handle other kinds of special errors like we're handling AssertionError right now
* Figure out how muliple imports/requires will be handled
* Write some tests
* 