Integrate SAWO in React Component
=================================

React is a free and open-source front-end JavaScript library for building user interfaces or UI components. A Component is one of the core building blocks of React.

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

1. As the first step to getting our React App to run with SAWO Component login, we need an essential component, which is the “SAWO API key”. You are probably wondering where we can get these, right? For that, we have to create a project in the SAWO Dashboard, where we can go directly by clicking `here <https://dev.sawolabs.com/>`__.

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

     npm i sawo-react
     
We have to go to the folder where we have created the React-component application and run the code in the terminal, which will install the SAWO package.

4. We have to initialize SAWO and render the form according to the following steps:

- Firstly, we have to define a callback function. The following code will help to do that:

.. code-block:: none

    function sawoLoginCallback(payload) {
            console.log(payload)
        }

- Next, we have to make an object. The code given below should help in the same.

.. code-block:: none

      const sawoConfig = {
              onSuccess: sawoLoginCallback, //required
              identifierType: 'email', //required must be one of: 'email', 'phone_number_sms',
              apiKey: '', //required get it from sawo dev.sawolabs.com,
              containerHeight: '300px', //required the login container height, default is 300px
          }
          
 This code will form the object, and will also style it according to the default structure.
 
       - Every added custom field should be accompanied by an 65px increase in the component height.

- Now, we have to add the react component to the main page where the Login Component has to render. The following code does that:

.. code-block:: none
   
   <SawoLogin config={sawoConfig}/>
   
5. Once, we have set up our project by integrating all of the above steps, the code block will look like this:

.. code-block:: none

     import React, { useEffect } from 'react'
     import SawoLogin from 'sawo-react'

     const LoginPage = () => {

         function sawoLoginCallback(payload) {
             console.log(payload)
         }

         const sawoConfig = {
             onSuccess: sawoLoginCallback //required,
             identifierType: 'email' //required, must be one of: 'email', 'phone_number_sms',
             apiKey: '' // required, get it from sawo dev.sawolabs.com,
             containerHeight: '300px', // the login container height, default is 300px
         }

         return (
             <div>
                 <SawoLogin config={sawoConfig}/>
             </div>
         )
     }

     export default LoginPage
     
This is the final code that we will add in the src folder of our application.

6. Once we successfully set up the SAWO SDK with the instructions above, we will get the SAWO login form in our application as shown below:

.. image:: ../images/Untitled%20(10).png

Congratulations! You have successfully integrated SAWO API Component with your React Application.

You can also check out the `Sample App <https://sawo-react-sample-app.netlify.app>`__.

Conclusion
----------

Hope you have enjoyed this short tutorial. We know this can be hard for a first-timer. If you got stuck, tell us where you got stuck in the #ask-for-help channel in our `official discord server <https://discord.com/invite/TpnCfMUE5P>`__, and our engineers will help you out.

*Enjoy with SAWO and we will see you next time.*
