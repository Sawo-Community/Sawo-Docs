Integrate SAWO in Android
=========================

Android software development is the process by which applications are created for devices running the Android operating system.

Let's get our Android App running with SAWO
===========================================

To get our app running, we need to have a few things installed.

Requirements
------------

JitPack [Version 0.1.8 ]

Let's move on to the steps.

Steps
-----

We need to follow a few steps to get SAWO integrated into our application.

1. As the first step to getting our Android App to run with SAWO login, we need an essential component, which is the “SAWO API key”. You are probably wondering where we can get these, right? For that, we have to create a project in the SAWO Dashboard, where we can go directly by clicking `here <https://dev.sawolabs.com/>`__.

1.1 Click the “create new project” button. Choose the platform on which we will create our project, where we will be able to see the code beforehand. In this case, it will be “Android” as we are creating it on Android. Click continue.

.. image:: ../images/SAWO%208.png

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

3. Firstly, we have to add the following line to the root of setting.gradle repositories block. The following code will help you do that.

.. code-block:: none

      maven { url 'https://jitpack.io' }
      
4. Next, we have to add the following code block to our app level build.gradle android block.  

.. code-block:: none

    compileOptions {
         sourceCompatibility JavaVersion.VERSION_1_8
         targetCompatibility JavaVersion.VERSION_1_8
     }

     kotlinOptions {
         jvmTarget = '1.8'
     }
     
5. After this, we have to add the following code block to our app level build.gradle dependencies block. 

.. code-block:: none

    implementation 'com.github.sawolabs:Android-SDK:0.1.8'
    
After we have done all of this. We will synchronize our entire project. 

6. Next, we have to create an Activity in Android Studio to get login success response. For this example, let's assume it is CallbackActivity.

7. Again, we have to add a button for login in the MainActivity. After that, we have to add the following code to its onclick handle. The following code is different for both Java and Kotlin. So, we will have a look at both of that.

Java
----

.. code-block:: none

      import com.sawolabs.androidsdk.Sawo;

      public void onClickLogin(View view) {
          new Sawo(
                      this, 
                      "", // your api key
                      ""  // your api key secret
                      ).login(
                      "email", // can be one of 'email' or 'phone_number_sms'
                      CallbackActivity.class.getName()  // Callback class name
              );
      }
      
Kotlin
------

.. code-block:: none

    import com.sawolabs.androidsdk.Sawo

    fun onClickLogin(view: View) {
             Sawo(
                 this,
                 "", // your api key
                 ""  // your api key secret
             ).login(
                 "email", // can be one of 'email' or 'phone_number_sms'
                 CallbackActivity::class.java.name // Callback class name
             )
         }
         
         
8. Lastly, we have to get the response payload in the CallbackActivity. For that, we have to add the following code. Again, the code will be different for both Java and Kotlin.

Java
----

.. code-block:: none

    import com.sawolabs.androidsdk.ConstantsKt;

    Intent intent = getIntent();
    String message = intent.getStringExtra(ConstantsKt.LOGIN_SUCCESS_MESSAGE);

    // continue with your implementation
    
Kotlin
------

.. code-block:: none

    import com.sawolabs.androidsdk.LOGIN_SUCCESS_MESSAGE

    val message = intent.getStringExtra(LOGIN_SUCCESS_MESSAGE)
    // continue with your implementation
    
9. Once we successfully set up the SAWO SDK with the instructions above, we will get the SAWO login form in our application as shown below:

.. image:: ../images/Untitled%20(10).png

Congratulations! You have successfully integrated SAWO with your Android Application. 

You can also check out the `Android Sample Code (Kotlin) <https://github.com/Sawo-Community/Sawo-Sample-Apps/tree/main/Android%20Integration>`__.

Conclusion
----------

Hope you have enjoyed this short tutorial. We know this can be hard for a first-timer. If you got stuck, tell us where you got stuck in the #ask-for-help channel in our `official discord server <https://discord.com/invite/TpnCfMUE5P>`__, and our engineers will help you out.

*Enjoy with SAWO and we will see you next time.*

