Integrate SAWO in Vue
=====================

Vue.js is an open-source model–view–ViewModel front-end JavaScript framework for building user interfaces and single-page applications.

Let's get our Vue App running with SAWO
========================================

To get our app running, we need to have a few things installed.

Requirements
------------

Node [Version 12.x+ ], Node Package Manager (NPM) [Version 6.x+]

Let's move on to the steps.

Steps
-----

We need to follow a few steps to get SAWO integrated into our application.

1. As the first step to getting our Vue App to run with SAWO login, we need an essential component, which is the “SAWO API key”. You are probably wondering where we can get these, right? For that, we have to create a project in the SAWO Dashboard, where we can go directly by clicking `here <https://dev.sawolabs.com/>`__.

1.1 Click the “create new project” button. Choose the platform on which we will create our project, where we will be able to see the code beforehand. In this case, it will be “web” as we are creating it on Vue. Click continue.

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

3. Firstly, while integrating SAWO SDK in our application, we have to install the Sawo package from the code given below:

.. code-block:: none

     npm i sawo
     
We have to go to the folder where we have created the Vue application and run the code in the terminal, which will install the SAWO package.

4. Next, we have to create a file "sawo.vue" in the components section of our application which will be available in the src folder. After creating, add this code snippet in the file which is given below:

.. code-block:: none

      <template>
      <div class="containerStyle">
      <section>
      <h2 class="title">VUE | Sawo Form Example</h2>
      <h2 class="title">User Logged In : {{ isLoggedIn }}</h2>
      <div class="loggedin" v-if="isLoggedIn">
      <h2>User Successfull login</h2>
      <div>UserId: {{ userPayload.user_id }}</div>
      <div>Verification Token: {{ userPayload.verification_token }}</div>
      </div>
      <div class="formContainer" id="sawo-container" v-if="!isLoggedIn">
      <!-- Sawo form will populate here -->
      </div>
      </section>
      </div>
      </template>
      <script>
      import Sawo from "sawo";

      export default {
      name: "Sawo",
      data: () => ({
      isLoggedIn: false,
      userPayload: {},
      Sawo: null,
      }),
      mounted() {
      const sawoConfig = {
      // should be same as the id of the container
      containerID: "sawo-container",
      // can be one of 'email' or 'phone_number_sms'
      identifierType: "email",
      // Add the API key
      apiKey: "API key",
      // Add a callback here to handle the payload sent by sdk
      onSuccess: (payload) => {
      this.userPayload = payload;
      this.isLoggedIn = true;
      console.log("Payload : " + JSON.stringify(payload));
      },
      };
      // creating instance
      this.Sawo = new Sawo(sawoConfig);
      this.Sawo.showForm();
      },
      };
      </script>
      
Here, replace the "API Key" with the API key that you have generated in the dashboard.
 
Also, you can see that after forming the template, we have imported the sawo class from the installed "sawo" package. The code given below determines it:

.. code-block:: none

    import Sawo from "sawo"
    
5. After this, we have to go to our "app.vue" file inside src. We have to add Sawo in your template here. Add the following line within template: 

.. code-block:: none

     <Sawo />

Then, within script, we have to import the "sawo" component from the "sawo.vue" file by adding the following line of code:

.. code-block:: none

    import Sawo from './components/Sawo.vue'
    
Lastly, we have to export the component alongside with your other components. So, under components within export default, add Sawo. A following example is given below:  
 
.. code-block:: none

      export default {
        name: 'App',
        components: {
          Home,
          Sawo
        }
      }
     
This is all you have to do.

6. If you have followed the above steps and integrated SAWO properly within your application, then you will see the SAWO dashboard generated on your application page as displayed in the picture below:

.. image:: ../images/Untitled%20(10).png

Congratulations! You have successfully integrated SAWO in your vue application.

You can also check out the `Vue Sample Code <https://github.com/Sawo-Community/Sawo-Sample-Apps/tree/main/Vue-Sample-App>`__ and `Sample App <https://sawo-vue-sample-app.netlify.app>`__.

Conclusion
----------

Hope you have enjoyed this tutorial and learned something from it. We know this can be hard for a first-timer. If you got stuck, tell us where you got stuck in the #ask-for-help channel in our `official discord server <https://discord.com/invite/TpnCfMUE5P>`__, and our engineers will help you out.

*Get your hands dirty with SAWO and we will see you next time.* 
