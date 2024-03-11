...

# Express API Deployed as Firebase Function

### Prerequesite

1. Google Firebase: Must have BLAZE PLAN and a project created

2. Google Firebase: Must have CLI tool installed, be logged in.

3. Install npm tools globally:`npm install -g firebase-tools`

(must have firebase BLAZE PLAN)

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
