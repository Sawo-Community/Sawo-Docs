Integrate SAWO in Bubble
========================

Bubble is a visual programming language, a no-code development platform and an application platform as a service, that lets us create web applications with no coding experience.

Let's get our Bubble App running with SAWO
==========================================

To get our app running, we need to have a few things installed.

Requirements
------------

For Bubble, we don't need any specific requirements.

Let's move on to the steps.

Steps
-----

We need to follow a few steps to get SAWO integrated into our application.

1. As the first step to getting our Bubble App to run with SAWO login, we need an essential component, which is the “SAWO API key”. You are probably wondering where we can get these, right? For that, we have to create a project in the SAWO Dashboard, where we can go directly by clicking `here <https://dev.sawolabs.com/>`__.

1.1 Click the “create new project” button. Choose the platform on which we will create our project, where we will be able to see the instructions beforehand. In this case, it will be “web” as we are creating it on Bubble. Click continue.

.. image:: ../images/SAWO%2011.png

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

3. To start with SAWO API Integration on Bubble, install the SAWO plugin from the marketplace.

4. Next, we have to locate the SAWO login under input forms and we will create a new login page. 

5. After this, we need to drag and drop the *sawo-login form*.

6. Afterwards, we have to double click on the form and select the identifier as 'email' or 'phone'.

.. image:: ../images/bubble%20gif.gif

7. To use SAWO Login, we will need an API key which we got from the dashboard.

8. Next, we will take a look at the workflow of the website.

Workflow of the website
-----------------------

To use email, we have to create two actions:

- 'user_signs_up'
- 'user_logs_in'

For the respective action, we need to *trigger* login or signup function.

      - For sawo ’login form A’s identifier, we will mention it as an email.
      - For sawo ’login form A’s password, we will mention it as a password.
      
To use phone number:

- Firstly, we have to append the custom text by making a Text ID.
- Next, we wil visit the language section and mention the domain '@xyz.in' against your Text ID.
- Lastly, we will use Phone number as email identifier.

9. Once we successfully set up the SAWO SDK with the instructions above, we will get the SAWO login form in our application as shown below:

.. image:: ../images/Untitled%20(10).png

Congratulations! You have successfully integrated SAWO with your Bubble Application.

Conclusion
----------

Hope you have enjoyed this short tutorial. We know this can be hard for a first-timer. If you got stuck, tell us where you got stuck in the #ask-for-help channel in our `official discord server <https://discord.com/invite/TpnCfMUE5P>`__, and our engineers will help you out.

*Enjoy with SAWO and we will see you next time.*
