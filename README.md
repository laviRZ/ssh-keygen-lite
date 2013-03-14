ssh-keygen
==========

Generates a SSH key-pair

### Install
1. Make sure you have ssh-keygen (try `$ ssh-keygen` if you aren't sure)
2. npm package install

```
npm install ssh-keygen
```
OR download from github and place in ./node_modules

### Usage



```
var keygen = require('ssh-keygen');
var fs = require('fs');

var location = __dirname + '/foo_rsa';
var comment = 'joe@foobar.com';
var password = 'keypassword'; // false and undefined will convert to an empty pw

keygen(location, comment, {
	password: password
}, function(err){
	if(err) return console.log('Something went wrong!');
	console.log('Keys created!')
	var private = fs.readFileSync( location );
	var public = fs.readFileSync( location + '.pub');
	console.log('private key: '+private);
	console.log('public key: '+public);
});

```

The following shell command will get executed:

```
$ ssh-keygen -t rsa -b 2048 -C "joe@foobar.com" -N "keypassword" -f ./foo_rsa
Generating public/private rsa key pair.
Your identification has been saved in ./foo_rsa.
Your public key has been saved in ./foo_rsa.pub.
The key fingerprint is:
02:f7:40:b6:c7:b3:a3:68:16:53:dd:86:63:df:b5:33 joe@foobar.com
The key's randomart image is:
+--[ RSA 2048]----+
|      o          |
|     o + o       |
|    . = O o   .  |
|     + = * . . . |
|    o . S . . E  |
|     + o .     o |
|    + .          |
|   o             |
|                 |
+-----------------+
```

### Note

It is advisable to generate your keys on a machine with a significant random source like one with a mouse/trackpad.

### License

ssh-keygen is [open source](https://github.com/ericvicenti/ssh-keygen/blob/master/LICENSE.md) under the MIT license

### Todo

* Real tests

Contributors welcome!