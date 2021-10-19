Integrate Sawo in Laravel
=========================

Laravel is a free, open-source PHP web framework. It mainly intends to develop web applications following the model–view–controller architectural pattern and based on Symfony.

Let's get our Laravel App running with SAWO
===========================================

To get our app running, we need to have a few things installed.

Requirements
------------

Packagist [Version 1.0.0 ], PHP [Version 7.2+ (~ 8.0.0)]

Let's move on to the steps.

Steps
-----

We need to follow a few steps to get SAWO integrated into our application.

1. As the first step to getting our Laravel App to run with SAWO login, we need an essential component, which is the “SAWO API key”. You are probably wondering where we can get these, right? For that, we have to create a project in the SAWO Dashboard, where we can go directly by clicking `here <https://dev.sawolabs.com/>`__.

1.1 Click the “create new project” button. Choose the platform on which we will create our project, where we will be able to see the code beforehand. In this case, it will be “web” as we are creating it on Laravel. Click continue.

.. image:: ../images/SAWO%201.png

1.2 Next, give the name of your project. In the “Enter your hostname” section, leave it empty because we will talk about it afterwards. Now, click “create”. There we are. We currently have a project in the SAWO dashboard.

.. image:: ../images/SAWO%203.png

1.3 Now, we can see in the project section the display of details about our project. Open notepad and copy the “API key” and and "Secret Key" because we will need it afterwards.

.. image:: ../images/SAWO%204.png

2. Once we create our project, we would need to set our hostname.

2.1 For development in a local machine, the hostname should be set to 'localhost'. So, write localhost beside the hostname and click "save". 

     - If using ''localhost" as hostname is not working for you, try "127.0.0.1"
.. image:: ../images/SAWO%205.png

2.2 For production, the hostname should be set to your domain.

     - If you are adding your domain, do not add 'https://', ''http://', 'www' or even trailing backslash. Example: We should keep https://dev.sawolabs.com/ as dev.sawolabs.com
.. image:: ../images/SAWO%206.png

3. Firsly, we have to install SAWO in our project. To get started with Sawo, we have to use the Composer package manager to add the package to our project's dependencies. The following code does that:

.. code-block:: none

    $ composer require sawolabs/sawo-laravel
    
4. Next, we have to do the configuration of SAWO. Before using Sawo, we will need to add credentials for our application. We should place these credentials in our application's config/sawo.php configuration file. Use the code snippet given below to do the same:

.. code-block:: none

      <?php

      return [
          /*
          |--------------------------------------------------------------------------
          | Configure Sawo defaults
          |--------------------------------------------------------------------------
          |
          | Supported Identifier Types: "phone_number_sms", "email"
          |
          */

          'api_key' => env('SAWO_API_KEY', ''),

          'api_secret_key' => env('SAWO_SECRET_KEY', ''),

          'identifier_type' => env('SAWO_IDENTIFIER_TYPE', 'email'),

          'redirect_url' => env('SAWO_REDIRECT', ''),
      ];
      
5. Afterwards, we have to create the .env file which will hold all of our sensitive informations. The content of the .env file should look something like this:

.. code-block:: none

    SAWO_API_KEY=<YOUR_SAWO_API_KEY_HERE>
    SAWO_SECRET_KEY=<YOUR_SAWO_SECRET_KEY_HERE>
    SAWO_IDENTIFIER_TYPE=phone_number_sms
    SAWO_REDIRECT=https://yourdomain.com/sawo/callback
    
We must replace the "yourdomain" with our domain name or simply put "localhost". We also have to put the API Key and Secret Key in the respective areas as cpoied from dashboard earlier.

6. For the next step, we have to add the Sawo login form to blade template. We will include the following code in our login blade template to show Sawo Auth dialog.

.. code-block:: none

     @include('sawo::auth')
     
7. Once we successfully set up the SAWO SDK with the instructions above, we will get the SAWO login form in our application as shown below:

.. image:: ../images/Untitled%20(10).png

Congratulations! You have successfully integrated SAWO with your Laravel Application.

You can also check out the `Laravel Sample Code <https://github.com/Sawo-Community/Sawo-Sample-Apps/tree/main/Laravel-example-app>`__.

Conclusion
----------

Hope you have enjoyed this short tutorial. We know this can be hard for a first-timer. If you got stuck, tell us where you got stuck in the #ask-for-help channel in our `official discord server <https://discord.com/invite/TpnCfMUE5P>`__, and our engineers will help you out.

*Enjoy with SAWO and we will see you next time.*
