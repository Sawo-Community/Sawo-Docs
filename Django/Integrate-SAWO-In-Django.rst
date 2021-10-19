Integrate SAWO in Django
========================

Django is a high-level Python Web framework that aids in rapid development and clean, realistic design. It reduces the hassle so we can focus on coding the app rather than reinventing the whole wheel.

Let's get our Django App running with SAWO
==========================================

To get our app running, we need to have a few things installed.

Requirements
------------

Python, pip (package-management system written in Python used to install and manage software packages)

Steps
-----

We need to follow a few steps to get SAWO integrated into our application.

1. As the first step to getting our Django App to run with SAWO login, we need an essential component, which is the “SAWO API key”. You are probably wondering where we can get these, right? For that, we have to create a project in the SAWO Dashboard, where we can go directly by clicking `here <https://dev.sawolabs.com/>`__.

1.1 Click the “create new project” button. Choose the platform on which we will create our project, where we will be able to see the code beforehand. In this case, it will be “web” as we are creating it on Django. Click continue.

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

3. The first step to getting started with SAWO API integration into our Django website/application is to install the sawo package as given below:

.. code-block:: none
   
    pip install sawo
    
We have to go to the folder where we have created the Flask application and run the code in the terminal, which will install the SAWO package.    

4. Next, we have to import createTemplate, getContext, and verifyToken methods from Sawo. The getContext method is used to create sawo dictionary object from data gain from Django Database. The ways to create the template and verify the token are given in subsequent steps. The following code does that:

.. code-block:: none

    from sawo import createTemplate, getContext, verifyToken
    
5. After this, we have to get started with the setup in Flask. The following steps will helps us do that:

- Firstly, we have to create a template for SAWO password-less and OTP-less Authentication for your Flask website. Use the code given below for the same:

.. code-block:: none

     createTemplate("./<filepath>",flask=True)
     #example
     createTemplate("./templates/partials",flask=True)

- Next, we have to send this data required by _sawo.html. The variable names used in _sawo.html template are sawo.auth_key, sawo.identifier and sawo.to Therefore, to send this data, we have to create a JSON.
    
    - The "to" route should be a post route that can receive posted data. If you don’t know how data is passed to templates in Django or Flask. We will suggest looking into it first. 

We have two methods to do this.

First Method sending Static Data
--------------------------------

- The following code sends the static data to your application:

.. code-block:: none

          context = {
                  "sawo":{
                          "auth_key": "<api_key>",
                          "identifier": "email | phone_number_sms"
                          "to": <route> #the route where you will receive
                          the payload sent by sdk                 
                  }
          }

          #example
          context = {
                  "sawo":{
                          "auth_key": "785ha-hdjsdsd-799-ss345",
                          "identifier": "email | phone_number_sms"
                          "to": login               
                  }
          }

Second Method using Admin and Database to save Config for SAWO
--------------------------------------------------------------

- We have to create the fields for SAWO api_key and identifier to set it from admin dashboard. For this, we have to copy the following code in the models of our app.

.. code-block:: none

     class Config(models.Models):
         api_key = models.CharField(max_length=200)
         identifier = models.CharField(max_length=200)
         choices = [("email","Email"),("phone_number_sms","Phone")]
         
- After this, we have to set up the view.py file of the app. We have to keep in mind that the Route should be the receiving end where we can handle post request. The following code will help us do that:

.. code-block:: none

     from models import Config
     from sawo import getContext

     def <your_function>(request):
         config = Config.objects.order_by('-api_key')[:1]
         context = {
             "sawo" = getContext(config,<route>) #the route where you will recieve
                     the payload sent by sdk    
         }


     #example

     def index(request):
         config = Config.objects.order_by('-api_key')[:1]
         context = {
             "sawo" = getContext(config,"login") 

         }
          
6. Once we successfully set up the SAWO SDK with the instructions above, we will get the SAWO login form in our application as shown below:

.. image:: ../images/Untitled%20(10).png

Congratulations!! The SAWO API is now ready to be used in your Flask application 🤘.

You can also check out the `Django Sample Code <https://github.com/Sawo-Community/Sawo-Sample-Apps/tree/main/Django-Sample-App>`__ and `Sample App <https://sawo-django-sample-app.herokuapp.com/>`__.

Conclusion
----------

Hope you have enjoyed this short tutorial. We know this can be hard for a first-timer. If you got stuck, tell us where you got stuck in the #ask-for-help channel in our `official discord server <https://discord.com/invite/TpnCfMUE5P>`__, and our engineers will help you out.

*Enjoy with SAWO and we will see you next time.*
