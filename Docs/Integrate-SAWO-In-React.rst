Integrate SAWO in React
=======================

React is a free and open-source front-end JavaScript library for building user interfaces or UI components. Facebook maintains it. We can build several practical applications through this library.

Let's get our React App running with SAWO
==========================================

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

1.3 Now, you can see in the project section the display of details about your project. Open notepad and copy the “API key” because you will need it afterwards.

.. image:: ../images/SAWO%204.png

2. Once we create our project, we would need to set our hostname.

2.1 For development in a local machine, the hostname should be set to 'localhost'. So, write localhost beside the hostname and click "save". 

     - If using ''localhost" as hostname is not working for you, try "127.0.0.1"
.. image:: ../images/SAWO%205.png

2.2 For production, the hostname should be set to your domain.

     - If you are adding your domain, do not add 'https://', ''http://', 'www' or even trailing backslash. Example: We should keep https://dev.sawolabs.com/ as dev.sawolabs.com
.. image:: ../images/SAWO%206.png

3. While integrating SAWO SDK in our application, firstly, we have to install the Sawo package from the code given below:

.. code-block:: none

     npm i sawo
     
We have to go to the folder where we have created the React application and run the code in the terminal, which will install the SAWO package.

4. Now, we have to create a file "login.js" in the src folder of our app, and add the following code:

.. code-block:: none

          import { useEffect } from 'react'
          import Sawo from 'sawo'

          const Login = () => {
              useEffect(() => {
                  var config = {
                      // should be same as the id of the container created on 3rd step
                      containerID: 'sawo-container',
                      // can be one of 'email' or 'phone_number_sms'
                      identifierType: 'phone_number_sms',
                      // Add the API key copied from 5th step
                      apiKey: 'API_KEY',
                      // Add a callback here to handle the payload sent by sdk
                      onSuccess: payload => {
                          console.log(payload);
                      },
                  }
                  let sawo = new Sawo(config)
                  sawo.showForm()
              }, [])

              return (

                  <div>
                      <div id="sawo-container" 
                      style={{
                      height: "300px", 
                      width: "400px",
                      }}
                      ></div>
                  </div>
              )
          }

          export default Login;
     
Here, we have to replace the API_KEY with the API key in our dashboard that we got earlier. 

5. Once we successfully set up the SAWO SDK with the instructions above, we will get the SAWO login form in our application as shown below:

.. image:: ../images/Untitled%20(10).png

Congratulations! You have successfully integrated SAWO with your React Application.

You can also check out the `React Sample Code <https://github.com/Sawo-Community/Sawo-Sample-Apps/tree/main/React-Sample-App>`__ and `Sample App <https://sawo-react-sample-app.netlify.app>`__.

Conclusion
----------

Oops! You got stuck! Don’t worry! We know this can be hard for a first-timer. Tell us where you got stuck in the #ask-for-help channel in our `official discord server <https://discord.com/invite/TpnCfMUE5P>`__, and our engineers will help you out.

*We hope you have enjoyed this article. Enjoy with SAWO and we will see you next time.*
