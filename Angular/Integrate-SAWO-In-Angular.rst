Integrating SAWO in your Angular App
====================================

Angular is a TypeScript-based free and open-source web application framework. It is a component-based framework for building scalable web applications.

Let's get our Angular App running with SAWO
===========================================

To get our app running, we need to have a few things installed.

Requirements
------------

Node [Version 12.x+ ], Node Package Manager (NPM) [Version 6.x+]

Let's move on to the steps.

Steps
-----

There are a few steps for us to follow for proper integration of SAWO into an Angular application.

1. As the first step to getting our Angular App to run with SAWO login, we need an essential component, which is the “SAWO API key”. You are probably wondering where we can get these, right? For that, we have to create a project in the SAWO Dashboard, where we can go directly by clicking `here <https://dev.sawolabs.com/>`__.

1.1 Click the “create new project” button. Choose the platform on which we will create our project, where we will be able to see the code beforehand. In this case, it will be “web” as we are creating it on Angular. Click continue.

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

We have to go to the folder where we have created the Angular application and run the code in the terminal, which will install the SAWO package.

4. We have to initialise SAWO and render the form according to the following steps:

- As part of this step, we have to create a container for the SAWO Component. We will do it in our project’s source file. The following code determines that:

.. code-block:: none
    
    <div id="sawo-container" style="height: 300px; width: 300px;"></div>

This shows the container ID and the style associated with it.

    - Every added custom field should be accompanied by an 50px increase in the component height.

- We have to check the configurations. The code given below should help in the same.

.. code-block:: none
    
  ngOnInit(){
    const sawoConfig = {
      // should be same as the id of the container
      containerID: "sawo-container",
      // can be one of 'email' or 'phone_number_sms'
      identifierType: "phone_number_sms",
      // Add the API key
      apiKey: "",
      // Add a callback here to handle the payload sent by sdk
      onSuccess: (payload: any) => {
        this.userPayload = payload;
        this.isLoggedIn = true;
      }
    };
    
Here, add the API Key that we copied from the dashboard.

- After this, we have to create a SAWO instance from the code given below.

.. code-block:: none

      this.Sawo = new Sawo(sawoConfig)

- Lastly, we have to call the showForm method as the showForm method is responsible for rendering the form in the given container.
