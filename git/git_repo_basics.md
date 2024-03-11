# Git Repo Video

## What is Git?

-version control for code



## Git...

installing...

recommen



## project setup...

1. Build new fold

2. Open folder in code editor

3. create some files as example code.

4. GIT SETUP:
   
   1. mainly used from command line
   
   2. COMMAND LINE is run inside a terminal.
   
   3. terminal is run in a specific place.

5. `cd ~/desktop/newFolder`

6. (terminal always starts in home directory)



### Getting started...

`git status` - Will return a summary of current state of git.

First step is to create first version.  Must do two things: 1. Choose which changes to incldue in the next version `git add filemjs` and then 2. Commit .

Shortcut to add all: `git add .`

QUESTION: Difference between git add . and giet add -A?

Git ADD does not create a new version.  It just allows us to select what to put in the new version.  A version is a "commit" (different name for same thing).  

May need to config!

`git config --global user.email "you@example.com"`

`git config --global user.name "Your Name"`

Then try again!



`git log` - shows version history

when gits are 'added', they are moved into the Staging Area.  All other changes go in the Working Area

STAGING AREA - pretty important apparently...

there is a button for "unstage"

..



### Visualizing Git... in VS Code...

iN EDITOR, make some changes after committing.

Go into the GIT sidebar, 

### GIT Cheatsheet...

COMMAND LINE BASICS:

`ls` or `dir`    -    list contents of current directory

`cd someFolder`    -    change directories to someFolder (must be in current directory)

`cd ~/Desktop/folder`    -    change directories absolute path from home (~)

GIT - GETTING STARTED

`git init`    -    start tracking all changes in current directory

`git status` - show all changes since previous version

`git add <file|folder>` - pick changes to go into next version

    `git add file` - pick individual file

    `git add folder/` pick all files inside a folder (and subfolders)

    `git add .` - pick all files (in folder command line is running in)

`git commit -m "Message"`- create a version with a message attached (message required)

`git commit -m "Message" --amend` - update previous commit instead of creating new one









...

# Git Repo Basics

### Prerequesites

1. github.com: create an account

2. ...

### Steps

1. create and navigate to empty folder and initialize:
   
   `mkdir expressFirebaseFunction`
   
   `cd expressFirebaseFunction`
   
   `firebase init`

2. Follow prompts in terminal to create project:
   
   select `Functions: Configure a Cloud Funciotions directory...`
   
   select `existing function`
   
   select `JavaScript`
   
   use esLing `no` (up to you!)
   
   install dependencies: `yes` 
   
   ~ you should get prompt 'Firebase initialization complete!' or similar
   
   start VS Code here to see projec that was created : `code .`

3. Open terminal in VS code, navigate into 'functions' folder and install dependencies
   
   `cd functions`
   
   `npm install express cors helmet`

4. Update functions/index.js
   
   delete boilerplate, then copy/paste into file:
   
   ```const
   // imports
   const functions = require("firebase-functions")
   const logger = require("firebase-functions/logger");
   const express = require("express");
   const cors = require("cors");
   const helmet = require("helmet");
   
   // initialize express app
   const app = express();
   app.use(express.json());
   app.use(cors());
   app.use(helmet());
   
   // set home route (and other routes)
   app.get('/',(req,res) => {
       res.send('Hello World')
   });
   
   // on request to deployed function, return the express app
   exports.api = functions.https.onRequest(app);
   ```

5. Navigate to main folder and deploy
   
   `cd ..` (NOT functions subfolder)
   
   `firebase deploy --only functions`

### Links

Github Repo:

I would love ANY feedback: Feedback Form
