#Advanced Installation on Windows.

First some possible dependency that you may encounter later:

- [**Python 2.7**](https://www.python.org/downloads/ "Python 2.7.*")
- [**Visual Studio for "VCBuild"**](http://www.visualstudio.com/en-us/products/free-developer-offers-vs "Visual Editor")

You may never require Python or Visual Studio for alot of your projects, but if your project requires compiling you will them need Bcrypt or Node-gyp.

For Windows, [**NVM**](https://github.com/creationix/nvm "NVM") you will need to use the *GOLANG CLI* version [**NVM Windows**](https://github.com/coreybutler/nvm-windows "NVM for Windows")

Download [**NVM for Windows**](https://github.com/coreybutler/nvm-windows "NVM for Windows") and follow their instructions for install.
> I recommend, that you install NVM to a root path like `` c:/nvm `` instead of installing in the roaming app folder. You can keep the NODEJS in the "Program Files" directory... If you desire.

After it is installed, go to *start*, search for **"system environment"**, and click the *"Edit the system environment variables"*. This should bring up the **System Properties** dialog box.

Click the button that says **Environment Variables** and within this new dialog box look through ``System variables`` for a Variable named Path. Select *Path* and click *Edit..* right below. A new dialog box will show up, and now in the input field named **Variable value** you should find at the end of the string `` %NVM_HOME%;%NVM_SYMLINK% ``.

This will indicate that you have installed it correctly, You can then check the ``System variables`` for ``NVM_HOME`` and ``NVM_SYMLINK``. This should point to the location you have installed them too.

Now that NVM is installed you can now install any version that is available.
In command line run: ``` nvm list available ``` to gain a list of the most stable and unstable versions out there.
Running ``` npm install 0.10.35 32 ``` will install the 32 bit version, as running ``` npm install 0.10.35 64 ``` will install the 64 bit version. To use that version you have installed run, ``` nvm use 0.10.35 32 ``` or 64.

> Please note that as I was running the commands above, I had to use the top row number keys as they weren't working with my number pad.

Next run in command line:
```
cd %NVM_SYMLINK%
```
and then: 
```
npm install npm
```

This command will set NPM to be installed here, and all global node apps installed like:

- Sails Js
- Coffee-Script
- Typescript

Will be under this directory that is held within the ``System variables`` *Path* variable.

If you have two versions of Python `` 2.7 and 3.2 `` your installed Node's NPM can give you a Python version error to solve this you can use ``` npm config set python x:/path_to_python/python.exe ``` that or if Python27 is available in the *Path* variable you can use ``` npm config set python python27 ```.
