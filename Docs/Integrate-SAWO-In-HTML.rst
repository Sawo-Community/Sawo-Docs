Integrating SAWO in your HTML Web Page
======================================

It’s your first project, and you are pretty excited to integrate SAWO login into your web page that you had recently created with HTML, or you are thinking of doing the same. But you don’t know where to start. Don’t worry! We are here to help you.

For some of you who are a complete newbie and are wondering what HTML is, let me give you an understanding. The HyperText Markup Language or HTML is the standard markup language for documents designed to display in a web browser.

*So, let’s get your HTML running with SAWO.*

Steps
=====

We need to follow a few steps to get the SAWO SDK integrated in our HTML page.

1. As the first step to getting our HTML page to run with SAWO login, we need an essential component, which is the “SAWO API key”. You are probably wondering where we can get these, right? For that, we have to create a project in the SAWO Dashboard, where we can go directly by clicking `here <https://dev.sawolabs.com/>`__.

1.1 Click the “create new project” button. Choose the platform on which we will create our project, where we will be able to see the code beforehand. In this case, it will be “web” as we are creating it on HTML. Click continue.

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

3. For the third step, we have to return to the HTML source code (where you have written or will write your HTML code). There, in the body tag (*<body>script</body>*), you have to put the following code. You can put the ID according to your will but remember it, as we will need it in the next step. This ID will be our "Container ID".

.. code-block:: none
    
    <div id="sawo-container" style="height: 300px; width: 300px;"></div>
    
4. After this, we have to add the following snippet at the bottom of the source code inside the body tag for the fourth step. The following code will invoke the SAWO API in your project.  

.. code-block:: none

          <script src="https://websdk.sawolabs.com/sawo.min.js"></script>
          <script>
          var config = {
          // should be same as the id of the container created on 3rd step
          containerID: "sawo-container",
          // can be one of 'email' or 'phone_number_sms'
          identifierType: "phone_number_sms",
          // Add the API key copied from 1st step
          apiKey: "",
          // Add a callback here to handle the payload sent by sdk
          onSuccess: (payload) => {
          console.log(payload)
          },
          };
          var sawo = new Sawo(config);
          sawo.showForm();
          </script>
          
Here, put the API Key in *apiKey: ""* that we got from the dashbaord.          

5. Once we successfully set up the SAWO SDK, a login form will be rendered in the provided container, as displayed in the picture below:

.. image:: ../images/Untitled%20(10).png

Congratulations !! You have made it. SAWO Login is now ready to be used on your HTML page.

You can also check out SAWO's HTML Sample Code `here <https://github.com/sawolabs/html-example>`__.

Conclusion
==========

Oops! You got stuck! Don’t worry! We know this can be hard for a first-timer. Tell us where you got stuck in the #ask-for-help channel in our `official discord server <https://discord.com/invite/TpnCfMUE5P>`__, and our engineers will help you out.

*We hope you have enjoyed this article. Play with SAWO and we will see you next time.*
    
