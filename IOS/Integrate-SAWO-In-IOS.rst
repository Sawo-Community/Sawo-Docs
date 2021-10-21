Integrate SAWO in iOS
=====================

iOS is a mobile operating system created and developed by Apple Inc. exclusively for its hardware.

Let's get our iOS App running with SAWO
=======================================

Integration of SAWO in iOS doesn't require any additional requirements. So, we will move on to the steps.

Steps
-----

We need to follow a few steps to get SAWO integrated into our application.

1. As the first step to getting our iOS App to run with SAWO login, we need an essential component, which is the “SAWO API key”. You are probably wondering where we can get these, right? For that, we have to create a project in the SAWO Dashboard, where we can go directly by clicking `here <https://dev.sawolabs.com/>`__.

1.1 Click the “create new project” button. Choose the platform on which we will create our project, where we will be able to see the code beforehand. In this case, it will be “iOS” as we are creating it on iOS. Click continue.

.. image:: ../images/SAWO%20IOS.png

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

3. Firstly, we will see the iOS CocoaPod Integration.

.. image:: ../images/New%20Xcode%20Project.png

4. Next, we will choose app in app templates.

.. image:: ../images/Select%20app%20template%20(1).png

5. Next, we will add unique Bundle Identifier.

.. image:: ../images/Bundle%20Identifier.png

6. Next, we will create an Apple Developer account ID and login.

7. After that, we have to select Identifiers and click '+' icon.

.. image:: ../images/Add%20Identifier.png

8. Next, we will select App IDs in Certificates, Identifiers & Profiles Tab.

.. image:: ../images/App%20IDs.png

9. Next, we will select App as a type.

.. image:: ../images/Select%20app%20template.png

10. After this, we have to add our bundle ID mentioned in the project created and description. Then, we will select App groups in the capabilities.

.. image:: ../images/Select%20app%20groups%20capabilty.png

11. Next, we will go to signing and capabilities and select teams with apple developer account linked to it and will click on capabilities button.

.. image:: ../images/Select%20apple%20developer%20account%20in%20team.png

12. Next, we have to select app groups in capabilities.

.. image:: ../images/Select%20app%20groups%20in%20capabilities.png

13. Next, we will add App group - “ ”.

.. image:: ../images/Add%20app%20group.png

14. We also have to keep in mind that, SawoFramework is available through `CocoaPods <https://cocoapods.org/>`__.

15. For the next step, we will create a new Xcode Project with a View Controller and create a login button and its action in the ViewController.swift file.

16. Next, we will open our project folder in terminal and type in 'pod init', then open the pod file of our project and add the following line to the pod file and save it.

.. code-block:: none

    pod 'SawoFramework'
    
17. Now, we will go back to the terminal, and type pod install to install the pod to our project. Once the pod has been installed, it will run the xcworkspace file of our project and work on it.    

18. Now, we have to import the framework and pod by adding the following code:

.. code-block:: none

     import UIKit
     import SawoFramework 
     
19. Next, we will add the following snippet above viewDidLoad func:

.. code-block:: none

     let VC = SawoFramework.LoginViewController()
     var PayloadApi = ""

     var publicKeyApp = ""
     var privateKeyApp = ""
     var sessionIdApp = ""


     var keychainPublicKEY = ""
     var keychainPrivateKEY = ""
     var keychainSessionID = ""
     
20. Next, we will add the following code snippet in your @IBAction func of the button:

.. code-block:: none

          self.present(self.VC, animated: true, completion: nil)

          let apiKey = ["apikey": "ADD-API-KEY-HERE"]
          let identifierType = ["identifier": "ADD-IDENTIFIER-HERE"]
          let secretKey = ["secretkey": "ADD-SECRET-KEY-HERE"]


          var userDefaults = UserDefaults(suiteName: "group.Trusted.SawoLabs.onesignal")
          if let testpublicKEY = userDefaults?.object(forKey: "publicKEY") as? String {
              //print("publicKEY : \(testpublicKEY)")
              keychainPublicKEY = testpublicKEY
          }
          if let testprivateKEY = userDefaults?.object(forKey: "privateKEY") as? String {
              //print("publicKEY : \(testprivateKEY)")
              keychainPrivateKEY = testprivateKEY
          }
          if let testsessionID = userDefaults?.object(forKey: "sessionID") as? String {
              //print("publicKEY : \(testsessionID)")
              keychainSessionID = testsessionID
          }

          let keychainPuK = ["keychainPuk": "\(String( keychainPublicKEY ))"]
          let keychainPrK = ["keychainPrk": "\(String( keychainPrivateKEY ))"]
          let keychainSess = ["keychainSess": "\(String( keychainSessionID ))"]


          NotificationCenter.default.post(name: Notification.Name("ProductKey"), object: nil,userInfo: apiKey)
          NotificationCenter.default.post(name: Notification.Name("IdentifierType"), object:nil, userInfo: identifierType)
          NotificationCenter.default.post(name: Notification.Name("SecretType"), object:nil, userInfo: secretKey)
          NotificationCenter.default.post(name: Notification.Name("keychainPuKFramework"), object: nil,userInfo: keychainPuK)
          NotificationCenter.default.post(name: Notification.Name("ProductKeyFramework"), object: nil,userInfo: keychainPrK)
          NotificationCenter.default.post(name: Notification.Name("keychainSessFramework"), object: nil,userInfo: keychainSess)

          NotificationCenter.default.addObserver(self, selector: #selector(SessionIDApp(_:)), name: Notification.Name("sessionId"), object: nil)
          
21. Next, we will add the following code in viewDidLoad func:

.. code-block:: none

     NotificationCenter.default.addObserver(self, selector: #selector(WebViewError(_:)), name: Notification.Name("WebViewError"), object: nil)
     NotificationCenter.default.addObserver(self, selector: #selector(LoginIsApproved(_:)), name: Notification.Name("LoginApproved"), object: nil)
     NotificationCenter.default.addObserver(self, selector: #selector(loginCONTENTapi(_:)), name: Notification.Name("PayloadOfUser"), object: nil)

     NotificationCenter.default.addObserver(self, selector: #selector(PublicKEYApp(_:)), name: Notification.Name("publickey"), object: nil)
     NotificationCenter.default.addObserver(self, selector: #selector(PrivateKEYApp(_:)), name: Notification.Name("privatekey"), object: nil)
     NotificationCenter.default.addObserver(self, selector: #selector(SessionIDApp(_:)), name: Notification.Name("sessionId"), object: nil)

     NotificationCenter.default.addObserver(self, selector: #selector(loginButtonWebView(_:)), name: Notification.Name("loginButtonPressed"), object: nil)
     
22. Next, we will add a new View Controller to which you want to take your user after login. After that, we will create a Segue to this View Controller and select its type as present modally. Inside Attributes inspector in presentation select full screen and give the segue a name in identifier. 

23. After this, we will add the snippet below viewDidLoad func.

.. code-block:: none

     @objc func loginButtonWebView(_ notification: Notification){
     //                DispatchQueue.main.asyncAfter(deadline: .now() + 6.0) {
     //                self.dismiss(animated: true, completion: nil)
     //                }
     //        performSegue(withIdentifier: "InternetError", sender: nil)
     }


     @objc func LoginIsApproved(_ notification: Notification){
         print("Login was Successful")
         self.dismiss(animated: true, completion: nil)
         performSegue(withIdentifier: "Sawo", sender: nil)
     }


     @objc func loginCONTENTapi(_ notification: Notification){
         if let data = notification.userInfo as? [String: String]
             {
                 for (UserPayload, Content) in data
                 {
                     PayloadApi = Content
                     print("\(UserPayload) : \(Content) ")
                 }
         }

     }

     @objc func PublicKEYApp(_ notification: Notification){
         if let data = notification.userInfo as? [String: String]
             {
                 for (PublicKEYApps, valuePublic) in data
                 {
                     publicKeyApp = valuePublic
                     print("\(PublicKEYApps) : \(valuePublic) ")
                     var userDefaults = UserDefaults(suiteName: "group.Trusted.SawoLabs.onesignal")!
                     userDefaults.set("\(valuePublic)", forKey: "publicKEY")
                     userDefaults.synchronize()

                 }
         }
     }

     @objc func PrivateKEYApp(_ notification: Notification){
         if let data = notification.userInfo as? [String: String]
             {
                 for (PrivateKEYApps, valuePrivate) in data
                 {
                     privateKeyApp = valuePrivate
                     print("\(PrivateKEYApps) : \(valuePrivate) ")
                     var userDefaults = UserDefaults(suiteName: "group.Trusted.SawoLabs.onesignal")!
                     userDefaults.set("\(valuePrivate)", forKey: "privateKEY")
                     userDefaults.synchronize()

                 }
         }
     }

     @objc func SessionIDApp(_ notification: Notification){
         if let data = notification.userInfo as? [String: String]
             {
                 for (SessionIDApps, valueSessionID) in data
                 {
                     sessionIdApp = valueSessionID
                     print("\(SessionIDApps) : \(valueSessionID) ")
                     var userDefaults = UserDefaults(suiteName: "group.Trusted.SawoLabs.onesignal")!
                     userDefaults.set("\(valueSessionID)", forKey: "sessionID")
                     userDefaults.synchronize()

                 }

         }


     }

     @objc func WebViewError(_ notification: Notification){
         print("Web View Error Recorded")
         performSegue(withIdentifier: "InternetError", sender: nil)
     }

     }

24. Next, we have to add values to the places marked in the comments.

25. Lastly, we have to keep in mind that the PayloadApi variable contains the user's payload.

26. Once we successfully set up the SAWO SDK with the instructions above, we will get the SAWO login form in our application as shown below:

.. image:: ../images/Untitled%20(10).png

Congratulations! You have successfully integrated SAWO with your iOS Application.

You can also check out SAWO's `iOS Sample Code <https://github.com/Sawo-Community/Sawo-Sample-Apps/tree/main/ios-framework>`__.

Conclusion
----------

Hope you have enjoyed this short tutorial. We know this can be hard for a first-timer. If you got stuck, tell us where you got stuck in the #ask-for-help channel in our `official discord server <https://discord.com/invite/TpnCfMUE5P>`__, and our engineers will help you out.

*Enjoy with SAWO and we will see you next time.*
