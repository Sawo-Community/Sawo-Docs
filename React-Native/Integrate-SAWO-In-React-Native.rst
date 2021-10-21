Integrate SAWO in React-Native
==============================

React Native is an open-source mobile application framework created by Facebook, Inc. It is used to develop applications for Android, Android TV, iOS, macOS, tvOS, Web, Windows and UWP.

Let's get our React App running with SAWO
==========================================

To get our app running, we need to have a few things installed.

Requirements
------------

Node Package Manager (NPM) [Version 1.0.0], React-Native [Version 0.64.0], React-Navigation, React-Native-Webview

Let's move on to the steps.

Steps
-----

We need to follow a few steps to get SAWO integrated into our application.

1. As the first step to getting our React App to run with SAWO login, we need an essential component, which is the “SAWO API key”. You are probably wondering where we can get these, right? For that, we have to create a project in the SAWO Dashboard, where we can go directly by clicking `here <https://dev.sawolabs.com/>`__.

1.1 Click the “create new project” button. Choose the platform on which we will create our project, where we will be able to see the code beforehand. In this case, it will be “web” as we are creating it on React. Click continue.

.. image:: ../images/SAWO%2010.png

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

3. Before getting started, we have to ensure if react-navigation is properly installed, if not we have to follow the React Navigation installation guide by clicking `here <https://reactnavigation.org/docs/getting-started/>`__.

4. We have to check for 'react-native-webiew'. It is a required package for Sawo as currently, auto linking for package dependancy is not there in react-native. Install it with the following code:

.. code-block:: none

     npm i react-native-webview
     
We have to go to the folder where we have created the React-Native application and run the code in the terminal, which will install the 'react-native-webview'.

5. To get started with Sawo, we will use the npm to add the package to your project's dependencies:

.. code-block:: none

    $ npm install react-native-sawo
    
6. Next, we have to import Sawo package in our project. Use the following code for that:

.. code-block:: none

     import Sawo from 'react-native-sawo';
     
7. After this, we will configure the route by using the following code block:

.. code-block:: none

      import {NavigationContainer} from '@react-navigation/native';
      import {createStackNavigator} from '@react-navigation/stack';

      <NavigationContainer>
          <Stack.Navigator>
              <Stack.Screen
                name="YOUR_LOGIN_ROUTE"
                component={Sawo}
                options={{
                  title: 'OTP Login',
                  headerShown: false, // by default its true, to hide the header
                }}
              />
          </Stack.Navigator>
      </NavigationContainer>
      
8. Afterwards, when calling route, we need to pass required credentials and a callback method to receive the user login data. We will use the code given below:

.. code-block:: none

    navigation.navigate('YOUR_LOGIN_ROUTE', {
        apiKey: 'YOUR_API_KEY',
        secretKey: 'YOUR_SECRET_KEY',
        identifierType: '', // email | phone_number_sms,
        callback: data => {}
    });
    
Here, we have to replace the YOUR_API_KEY and YOUR_SECRET_KEY with the API key and Secret Key in our dashboard that we got earlier.  

9. Once we successfully set up the SAWO SDK with the instructions above, we will get the SAWO login form in our application as shown below:

.. image:: ../images/Untitled%20(10).png

Congratulations! You have successfully integrated SAWO with your React-Native Application.

You can also check out the `React Sample Code <https://github.com/Sawo-Community/Sawo-Sample-Apps/tree/main/React-Native-Sample-App>`__.

Conclusion
----------

Hope you have enjoyed this short tutorial. We know this can be hard for a first-timer. If you got stuck, tell us where you got stuck in the #ask-for-help channel in our `official discord server <https://discord.com/invite/TpnCfMUE5P>`__, and our engineers will help you out.

*Enjoy with SAWO and we will see you next time.*
