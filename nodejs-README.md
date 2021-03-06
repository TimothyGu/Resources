# Learn Session 3: Backend Web Development with Node.JS

## Table of Contents:
### Learn Session:
1. What is Node.js?
2. Installing Node.js
3. Creating a new node.js application
   * [Hello, World Tutorial](https://github.com/acm-hackschool-f17/Resources/blob/master/nodejs-README.md#creating-a-new-nodejs-application)

### Installing Node.js
#### On Windows

1. Go to https://nodejs.org/en/
2. Click on green "8.8.1 Current" button to download installer
3. Install the downloaded `.msi` file

#### On macOS and Linux-based systems

1. Go to https://github.com/creationix/nvm
2. Copy the instructions for Wget, and run it in the command line
   ```
   $ wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.6/install.sh | bash
   => Downloading nvm from git to '/home/your-username/.nvm'
   => Cloning into '/home/your-username/.nvm'...
   ...

   => Compressing and cleaning up git repository

   => Appending nvm source string to /home/your-username/.bashrc
   => Appending bash_completion source string to /home/your-username/.bashrc
   => Close and reopen your terminal to start using nvm or run the following to use it now:

   export NVM_DIR="$HOME/.nvm"
   [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
   [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
   ```
3. Close the terminal and relaunch it, and run `nvm install 8`
   ```
   $ nvm install 8
   Downloading and installing node v8.8.1...
   Downloading https://nodejs.org/dist/v8.8.1/node-v8.8.1-linux-x64.tar.xz...
   ######################################################################## 100.0%
   Computing checksum with sha256sum
   Checksums matched!
   Now using node v8.8.1 (npm v5.4.2)
   ```

### Creating a new node.js application
#### Steps:
1. On your command line navigate to a new folder where you want to save your project files.
2. `npm init`
   * Go through the steps in this including setting a project name, description, version, etc. Feel free to leave things blank because not everything is neccesary.
     ```
     $ npm init
     This utility will walk you through creating a package.json file.
     ...
     name: (temp) some-title
     version: (1.0.0)
     description: some-description
     entry point: (index.js) server.js
     test command:
     git repository:
     keywords:
     author: my-name
     license: (ISC)

     ...

     {
       "name": "some-title",
       "version": "1.0.0",
       "description": "some-description",
       "main": "server.js",
       "scripts": {
         "test": "echo \"Error: no test specified\" && exit 1"
       },
       "author": "my-name",
       "license": "ISC"
     }

     Is this ok? (yes)
     ```
   * A file called `package.json` will be created. `package.json` is a file most importantly listing the external libraries your project has installed. Libraries are installed into a folder in your project directory NPM makes called `node_modules`.
3. `npm install express --save`
   * This adds a new dependency to your `package.json` called express (a library to simplify creating an HTTP server).
   * This code block will be added near the bottom of `package.json`
     ```
     "dependencies": {
      "express": "^4.16.2"
     }
     ```
4. `touch server.js`
5. Add the following code to `server.js`.
    ```
    // Imports the library "express"
    const express = require('express');

    // Creates an instance of the HTTP server
    const app = express();

    // Creates an endpoint at your web application's root.
    // An endpoint is a way to connect the client and server by
    // means of a pathway URL.
    // Root in this case means there is no extended URL path
    // and to access the base directory of the server.
    // An example is https://github.com/ is the root endpoint
    // whereas https://github.com/acm-hackschool-f17/ has an
    // endpoint of /acm-hackschool-f17
    app.get('/', (req, res) => {
      res.send("Hello world");
    });

    app.get('/burrito', (req, res) => {
      res.send("Hello I am a burrito");
    });

    // Starts your server
    app.listen(3000, () => {
      console.log("Listening on port 3000");
    });
    ```
6. `node server.js`
   * this should run and stall your command prompt, which is correct behavior
     ```
     $ node server.js
     Listening on port 3000
     ```
7. Go to http://localhost:3000/ to see your server rendering "Hello world" on the page!
8. Go to http://localhost:3000/burrito to see your server rendering "Hello I am a burrito"!
