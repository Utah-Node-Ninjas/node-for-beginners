![Node.js](http://nodeblog.files.wordpress.com/2011/07/nodejs.png)

#node-for-beginners

*This is an official chapter of [NodeSchool.io](http://nodeschool.io). You can find the official repository [here](https://github.com/nodeschool/utahnodeninjas).*

An intro to Node.js Programming for absolute beginners, in connection with NodeSchool.io and our biweekly hack nights at Utah Node Ninjas meetup group. Every other wednesday at Utah Node Ninjas, we provide a free introduction to Node.js, taught by our organizers. This will serve a syllabus of sorts. If you have any questions, please feel free to reach out to any of the organizers of the group, and we can assist with any issues. 

##Contributing

If you wish to contribute to this guide, please fork the repo and create a pull request detailing the changes made. One of our organizers will review and merge as needed.

#Intro to Node

##What is Javascript?

JavaScript is a dynamic computer programming language. It is most commonly used as part of web browsers, whose implementations allow client-side scripts to **interact with the user**, **control the browser**, **communicate asynchronously**, and **alter the document content** that is displayed.

*It is assumed that you, as a beginner in this guide, have a basic understanding of Javascript as a programming language. If you are unfamiliar with Javascript at all, please first go through the tutorials at [Codecademy](http://www.codecademy.com/tracks/javascript) before continuing with this guide.*

##What is Node.js?

Node.js is a cross-platform runtime environment for server-side and networking applications. Node.js applications are written in JavaScript, and can be run within the Node.js runtime on OS X, Microsoft Windows and Linux with no changes. In short, it is **Javascript run on the server, rather than the browser**.

Node.js internally uses the Google V8 JavaScript engine to execute code, and a large percentage of the basic modules are written in JavaScript. Node.js contains a built-in asynchronous I/O library for file, socket, and HTTP communication, which allows applications to act as a Web server without software such as Apache HTTP Server or IIS.

Node.js is gaining adoption as a high-performance server-side platform and is notably used by Groupon, SAP, LinkedIn, Microsoft, Yahoo!, Walmart, Rakuten and PayPal.

##Why Node.js?
- It runs Javascript, so you can use the same language on server and client, and even share some code between them (e.g. for form validation, or to render views at either end.)

- The event-driven system is fast, compared to traditional Java or ROR frameworks, when handling lots of requests at once. The benchmarks for it blow older languages like PHP, Python and Ruby out of the water.

- The ever-growing pool of packages, accessible via NPM, most of which are conveniently hosted on github.

- It’s driven by asynchronous design. That means that it doesn’t have to wait for slow file I/O or database operations to continue processing, which makes it really damn fast (by that I mean faster than most other popular server languages / platforms). It also means that it can handle millions of concurrent connections at once.

- It makes real-time applications a walk in the park. No longer do you have to bother with low-level sockets and protocols. You can make a Comet-driven real-time chat application in the same time you would have made a simple blog in PHP or a birthday cake with a ready-made mix.

##Install Node
###Linux/Mac
There are a lot of different ways to install Node on Unix environments. Most of them *mostly* work. But you will run into various issues with many different things if Node is not installed in a very specific way. The one that I have found the most versitile is the install provided by [NVM](https://github.com/creationix/nvm), or the Node Version Manager.

Run the following command:
```bash
curl https://raw.githubusercontent.com/creationix/nvm/v0.17.2/install.sh | bash
```
Next, make sure the following is included in your ~/.bash_profile, ~/.bashrc, ~/.zshrc or ~/.profile:
```bash
if [ -f ~/.nvm/nvm.sh ]; then
  export NVM_DIR=$HOME/.nvm;
  source $HOME/.nvm/nvm.sh;
fi
```
Next, run this command:
```bash
nvm install 0.10
```
And finally this:
```bash
nvm use 0.10 --default
```
Now anytime your terminal loads, node should be included and ready to roll!

###Windows
*Installation Instructions for Windows needed. Contributions welcome!*


##Getting your hands dirty
***Congratulations!*** You now have node running on your system! You can now develop Node.js modules and applications as you please. At this point, we will be covering the course material outlined in the NodeSchool curriculum. 

To install the coursework, run the following command:
```bash
npm install -g learnyounode
```
To start the coursework, type in your console:
```bash
youlearnnode
```

There are a couple things that are not covered by the coursework. Those are listed below. 

##Moduling

*Taken from learnyounode*

Create a new module by creating a new file that just contains your directory reading and filtering function. To define a single function export, you assign your function to the module.exports object, overwriting what is already there:
```javascript
    module.exports = function (args) { /* ... */ }
```
Or you can use a named function and assign the name.

To use your new module in your original program file, use the require() call in the same way that you require('fs') to load the fs module. The only difference is that for local modules must be prefixed with './'. So, if your file is named mymodule.js then:
```javascript
    var mymodule = require('./mymodule.js')
```
The `.js` is optional here and you will often see it omitted.

You now have the module.exports object in your module assigned to the mymodule variable. Since you are exporting a single function, mymodule is a function you can call!

Also keep in mind that it is idiomatic to check for errors and do early-returns within callback functions:
```javascript
    function bar (callback) {
      foo(function (err, data) {
        if (err)
          return callback(err) // early return
    
        // ... no error, continue doing cool things with `data`
    
        // all went well, call callback with `null` for the error argument
    
        callback(null, data)
      })
    }
```

##NPM

Node Package Manager (NPM) is a NodeJS dependency manager. As its name would imply, you can use it to install node programs. Also, if you use it in development, it makes it easier to specify and link dependencies.

####Install

If you installed Node correctly, NPM should be installed with it. If not, run the following command:

```bash
curl http://npmjs.org/install.sh | sh
```

###Getting help: npm help
npm has a lot of help documentation about all of its commands. The `npm help` command is your best friend. You can also tack `--help` onto any npm command to get help on that one command.

###Installing stuff: npm install
`npm install blerg` installs the latest version of blerg. You can also give install a tarball, a folder, or a url to a tarball. If you run npm install without any arguments, it tries to install the current folder based on the package.json (we'll go over that later).

This command can do a lot of stuff. `npm help install` will tell you more than you ever wanted to know about it.

###Showing things: npm ls
The `npm ls` command shows what's on your system, and also what's available in the registry. The arguments are beautifully colored greps. For instance `npm ls installed` would show you what's installed on your system. `npm ls installed marak` would show you all the packages installed on your system created by Marak.

`npm help ls` for more info.

###Updating packages: npm update
The update command does a few things.

-Search the registry for new versions of all the packages installed.
-If there's a newer version, then install it.
-Point dependent packages at the new version, if it satisfies their dependency.
-Remove the old versions, if no other package names them as a dependency.

So basically, update behaves a lot like a "standard" package manager's update command, except that it also checks to make sure that the new version isn't going to break anything before it points stuff at it.

###Making a Package: The package.json file.
The package.json file goes in the root of your package. It tells npm how your package is structured, and what to do to install it.

Most of the time, you only need the "name", "version", and "main" fields (even for node-waf compiled addons).

Run `npm init` to Install the package.json file for you.

Use `npm help json` to learn which fields npm cares about. Basically, it's as simple as putting the package.json file in the root of your project, and then telling it how to get to your code.

###Development: npm link
The link command symlinks a package folder into your system, so that changes are automatically reflected. It also installs the "dependencies" and "devDependencies" packages from your package.json file.

This is one of the most useful tools for developing programs with node. Give your thing a name and a version in a package.json file. Specify a few dependencies and a main module. Then run `npm link`, and go to town coding it and testing it out in the node repl. It's great.

npm is a development tool, first and foremost. People sometimes say "Yeah, I haven't gotten time to check out that package manager stuff yet. Maybe I will when my code is more stable."

That's like saying that you're going to start using source control when your code is done. It's just silly. Source control should make your process easier, and if it doesn't, then you're using a broken SCM. Same for package management. It should make it easier, and if it doesn't, then something is wrong.

###Acquiring Fame: npm publish
So, you created a package, and you can install it. Now you want the everlasting fame and glory that comes with other people using your code. There is no better way to ensure your immortality than eventually being a part of every web app out there, and the best—nay, the ONLY—way to truly accomplish this is to publish nodejs packages.

First, create a user account with `npm adduser`. Give it a username, password, and email address, and it'll create an account on the npm registry. (You can also use adduser to authorize a user account on a new machine, or fix the situation if you break your configs.)

Next, go to the root of your package code, and do `npm publish`.

Bam. Done.

