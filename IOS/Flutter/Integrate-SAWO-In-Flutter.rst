Integrate SAWO in Flutter
=========================

Flutter is an open-source UI software development kit created by Google. It is used to develop cross-platform applications.

Let's get our Flutter App running with SAWO
===========================================

To get our app running, we need to have a few things installed.

Requirements
------------

We will not need any extra requirements for this integration.

Let's move on to the steps.

Steps
-----

We need to follow a few steps to get SAWO integrated into our application.

1. As the first step to getting our Flutter App to run with SAWO login, we need an essential component, which is the “SAWO API key”. You are probably wondering where we can get these, right? For that, we have to create a project in the SAWO Dashboard, where we can go directly by clicking `here <https://dev.sawolabs.com/>`__.

1.1 Click the “create new project” button. Choose the platform on which we will create our project, where we will be able to see the code beforehand. In this case, it will be “Hybrid” as we are creating it on Flutter. Click continue.

.. image:: ../images/SAWO%209.png

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

3. To get started with the integration of SAWO API on our Flutter App, we have to add the plugin in dependencies. Add the following code:

.. code-block:: none

    dependencies:
      sawo: ^0.1.2
      
4. After this, we have to install the plugin, by running the mentioned command:  

.. code-block:: none

    flutter pub get
    
We have to go to the folder where we have created the Flutter application and run the code in the terminal, which will install the plugin.

5. As part of the next step, we will import the plugin into class by using the code given below:

.. code-block:: none

    import 'package:sawo/sawo.dart';
    
6. Next, we will create a Sawo Instance. The following code will help to do that:

.. code-block:: none

    Sawo sawo = new Sawo(
        apiKey: <YOUR-API-KEY>,
        secretKey: <YOUR-Secret-Key>,
     );

7. Lastly, we have to redirect the user to the login page. The following code will help you do that:

.. code-block:: none

      // sawo object
      Sawo sawo = Sawo(
        apiKey: "Your API Key",
        secretKey: "Your Secret key",
      );

      // user payload
      String user = "";

      void payloadCallback(context, payload) {
        if (payload == null || (payload is String && payload.length == 0)) {
          payload = "Login Failed :(";
        }
        setState(() {
          user = payload;
        });
      }

      @override
      Widget build(BuildContext context) {
        return Center(
          child: Padding(
            padding: const EdgeInsets.symmetric(horizontal: 20),
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Text("UserData :- $user"),
                ElevatedButton(
                  onPressed: () {
                    sawo.signIn(
                      context: context,
                      identifierType: 'email',
                      callback: payloadCallback,
                    );
                  },
                  child: Text('Email Login'),
                ),
                ElevatedButton(
                  onPressed: () {
                    sawo.signIn(
                      context: context,
                      identifierType: 'phone_number_sms',
                      callback: payloadCallback,
                    );
                  },
                  child: Text('Phone Login'),
                ),
              ],
            ),
          ),
        );
      }
      
With this way, we will complete the SAWO setup.

      - SAWO provides two ways to authenticate users, one by email and one by phone number.
      - When a user is successfully verified, the callback method will get invoked with the payload which contains userID and when something is wrong the payload will be null.
      
8. Once we successfully set up the SAWO SDK with the instructions above, we will get the SAWO login form in our application as shown below:

.. image:: ../images/Untitled%20(10).png

Congratulations! You have successfully integrated SAWO with your Flutter Application.   

You can also check out the `React Sample Code <https://github.com/Sawo-Community/Sawo-Sample-Apps/tree/main/Flutter-SDK>`__.

Conclusion
----------

Hope you have enjoyed this short tutorial. We know this can be hard for a first-timer. If you got stuck, tell us where you got stuck in the #ask-for-help channel in our `official discord server <https://discord.com/invite/TpnCfMUE5P>`__, and our engineers will help you out.

*Enjoy with SAWO and we will see you next time.*
