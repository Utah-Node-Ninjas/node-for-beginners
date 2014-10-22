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
