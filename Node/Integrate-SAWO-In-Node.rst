Integrate SAWO in Node
======================

Node.js is an open-source, cross-platform, back-end JavaScript runtime environment that runs on the V8 engine and executes JavaScript code outside a web browser.

Let's get our Node App running with SAWO
========================================

To get our app running, we need to have a few things installed.

Requirements
------------

Node [Version 12.x+ ], Node Package Manager (NPM) [Version 6.x+]

Let's move on to the steps.

Steps
-----

We need to follow a few steps to get SAWO integrated into our application.

1. As the first step to getting our React App to run with SAWO login, we need an essential component, which is the “SAWO API key”. You are probably wondering where we can get these, right? For that, we have to create a project in the SAWO Dashboard, where we can go directly by clicking `here <https://dev.sawolabs.com/>`__.

1.1 Click the “create new project” button. Choose the platform on which we will create our project, where we will be able to see the code beforehand. In this case, it will be “web” as we are creating it on React. Click continue.

.. image:: ../images/SAWO%201.png

1.2 Next, give the name of your project. In the “Enter your hostname” section, leave it empty because we will talk about it afterwards. Now, click “create”. There we are. We currently have a project in the SAWO dashboard.

.. image:: ../images/SAWO%203.png

1.3 Now, we can see in the project section the display of details about our project. Open notepad and copy the “API key” because we will need it afterwards.

.. image:: ../images/SAWO%204.png

2. Once we create our project, we would need to set our hostname.

2.1 For development in a local machine, the hostname should be set to 'localhost'. So, write localhost beside the hostname and click "save". 

     - If using ''localhost" as hostname is not working for you, try "127.0.0.1"
.. image:: ../images/SAWO%205.png

2.2 For production, the hostname should be set to your domain.

     - If you are adding your domain, do not add 'https://', ''http://', 'www' or even trailing backslash. Example: We should keep https://dev.sawolabs.com/ as dev.sawolabs.com
.. image:: ../images/SAWO%206.png

3. To get started with the integration, we have to install express by running as a first. The following code helps in doing that

.. code-block:: none
    
    npm install express
    
We have to go to the folder where we have created the Node application and run the code in the terminal, which will install the SAWO package. 

4. Next, we have to make endpoints in index.js file and serve our HTML files.

.. code-block:: none

      const express = require("express");
      const app = express();

      const path = require("path");
      app.use(express.static(path.join(__dirname, "public")));

      app.get("/", (req, res) => {
        res.sendFile(__dirname + "/index.html");
      });

      app.get("/login", (req, res) => {
        res.sendFile(__dirname + "/public/login.html");
      });

      app.get("/success", (req, res) => {
        res.sendFile(__dirname + "/public/success.html");
      });

      app.listen("3000", console.log("Listening on port 3000."));
      
5. Lastly, we have to add the following code to the body of the HTML login page so that it should look like this for showing the SAWO login form: 

.. code-block:: none

      <body>
        <div id="sawo-container" style="height: 300px; width: 300px"></div>

        <script src="https://websdk.sawolabs.com/sawo.min.js"></script>
        <script>
          // Fetching payload from sessionStorage
          const payload = sessionStorage.getItem("payload");
          if (payload) {
            // If the payload is available, that means the user has logged in already.
            // So redirecting back to "/login"
            window.location.href = "/success";
          }
          var config = {
            // should be same as the id of the container created earlier
            containerID: "sawo-container",
            // can be one of 'email' or 'phone_number_sms'
            identifierType: "email",
            // Add the API key copied from dashboard
            apiKey: "Your API Key",
            // Add a callback here to handle the payload sent by sdk
            onSuccess: (payload) => {
              // Storing the payload in sessionStorage
              sessionStorage.setItem("payload", JSON.stringify(payload));
              // Redirecting to "/success"
              window.location.href = "/success";
            },
          };
          var sawo = new Sawo(config);
          sawo.showForm();
        </script>
      </body>

We must replace "Your API Key" with the API Key that we copied earlier.

      - You can store the payload to the sessionStorage, database, or integrate CRM and can take actions according to that.
      
6. Once we successfully set up the SAWO SDK with the instructions above, we will get the SAWO login form in our application as shown below:

.. image:: ../images/Untitled%20(10).png

Congratulations! You have successfully integrated SAWO with your Node Application. 

You can also check out the `Nodejs Sample Code <https://github.com/Sawo-Community/Sawo-Sample-Apps/tree/main/Nodejs-sample-app>`__.

Conclusion
----------

Hope you have enjoyed this short tutorial. We know this can be hard for a first-timer. If you got stuck, tell us where you got stuck in the #ask-for-help channel in our `official discord server <https://discord.com/invite/TpnCfMUE5P>`__, and our engineers will help you out.

*Enjoy with SAWO and we will see you next time.*
