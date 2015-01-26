#Advanced Installation on Windows.
These instructions are still in draft form and we hope to update them soon after
testing on multiple versions of Windows.  If you experience problems, please
create a github issue or better yet, submit a pull request with your corrections.

##Compiling Addons
[Node.js addons](http://nodejs.org/api/addons.html) require compilation with [node-gyp](https://github.com/TooTallNate/node-gyp).
 addons are dynamically linked shared objects that can provide glue to C/C++ libraries.
 This means that you can take pretty much any C/C++ library and create an addon that will allow you to use it in Node.js.

Install node-gyp using npm:

    npm install -g node-gyp

Node-gyp requires manually installing these additional dependencies:

* [**Python 2.7**](https://www.python.org/downloads/ "Python 2.7.*")
* [**Visual Studio for "VCBuild"**](http://www.visualstudio.com/en-us/products/free-developer-offers-vs "Visual Editor")

You may never require Python or Visual Studio for many your projects, but if your project requires compiling with node-gyp,
you will need them. For example, [bcrypt](https://www.npmjs.com/package/bcrypt) requires these dependencies.

## Installing NVM-Windows
The [official version of nvm](https://github.chttps://github.com/creationix/nvmom/creationix/nvm) is not technically available on windows.
However, there is an independently created version manager called [nvm-windows](https://github.com/coreybutler/nvm-windows "NVM for Windows").
Realize that some features of nvm may not be available on nvm-windows, since they are two entirely different projects.

Follow their instructions for installation, taking note of the following:
> I recommend, that you install NVM to a root path like `` c:/nvm `` instead of installing in the roaming app folder. You can keep the NODEJS in the "Program Files" directory... If you desire.

After it is installed, do the following to verify installation was successful:
* Go to Windows *start* button, search for **"system environment"**
* Click the *"Edit the system environment variables"* to bring up the **System Properties** dialog box.
* Click the button that says **Environment Variables**
* Within this new dialog box look through ``System variables`` for a Variable named Path.
* Select *Path* and click *Edit..* right below.
* A new dialog box will show up, and now in the input field named **Variable value** you should find at the end of the string `` %NVM_HOME%;%NVM_SYMLINK% ``.
* This will indicate that you have installed it correctly
* You can then check the ``System variables`` for ``NVM_HOME`` and ``NVM_SYMLINK``

Now that NVM is installed, you can now install any version that is available.
In command line run: ``` nvm list available ``` to gain a list of the most stable and unstable versions out there.
Running ``` npm install 0.10.35 32 ``` will install the 32 bit version, as running ``` npm install 0.10.35 64 ``` will install the 64 bit version. To use that version you have installed run, ``` nvm use 0.10.35 32 ``` or 64.

Next run in Git Bash:
```
cd $NVM_SYMLINK #Note: cd %NVM_SYMLINK% if using Windows default shell
```
and then: 
```
npm install npm
```

This step will set NPM to be installed here, along with all global node modules,
under this directory that is held within the ``System variables`` *Path* variable.

If you have two versions of Python `` 2.7 and 3.2 ``, npm may give you a
Python version error.  To solve this issue, you can execute
``` npm config set python x:/path_to_python/python.exe ```
or if Python27 is available in the *Path* variable you can use
``` npm config set python python27 ```
