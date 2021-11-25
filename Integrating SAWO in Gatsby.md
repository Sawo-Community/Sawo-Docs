# Integrating SAWO in a Gatsby 

## Gatsby:
* It helps to build a progressive Web Application,it is a React-based  open-source framework for making websites and apps. 
* It combines the management and measurability of dynamically rendered sites with the speed of static-site generation that helps developers build blazing quick websites and apps.

Let's Get your Gatsby running with SAWO 🙌

## Software Required:

* [Visual Studio Code](https://code.visualstudio.com/#alt-downloads)
* [Git](https://www.atlassian.com/git/tutorials/install-git)
* Gatsby command line 
* [Node.js](https://nodejs.org/en/) (v14.15 or newer) 

## Operating System:

- macOS Sierra or later (10.12)
- Windows 10 ([Setup Instructions](https://www.gatsbyjs.com/docs/how-to/local-development/gatsby-on-windows/))
- Linux ([Setup Instructions](https://www.gatsbyjs.com/docs/how-to/local-development/gatsby-on-linux/))

## Get Started

After satisfying all the requirements,we are good to go...

## Steps

## 0. Creating a Gatsby site
 First we have to create a Gatsby Site, refer to Gatsby Documentation

## 1. Generating a SAWO API key

  1.1 First we need to Create an account with SAWO
  -  Create an account with [SAWO](https://dev.sawolabs.com/) 
  -  If you are already part of SAWO Family & have an account then navigate to **[SAWO](https://dev.sawolabs.com/dash/dashboard)**

  1.2 Now **click on Create New Project** at the bottom left of the website and 
      select the platform you are looking to build your product on
      
  1.3 Now INTEGRATION ,Choose your required setup mode based on your preference and then just click onto continue
  
  1.4 Provide a name to your Project as per your choice
  
### Host Name

- As per your preferance you can choose either Undeployed or Deployed host

```shell

  (NOTE: for Undeployed Host your default LOCAL HOSTNAME  will be: "127.0.0.1")

```

- after this click on  **CREATE** , you will get your SAWO API Keys `csv` files Downloaded 


## 2. Integratating SAWO in Gatsby

   Now follow the following steps:

- **Install SAWO SDK**

```shell
  npm install sawo
  ```

- **Import SAWO SDK**:
 
 ```js
  import Sawo from 'sawo'
  ```

- **Import Classes**: to create a login page 
  
 ```js
  import React, { useEffect } from 'react'
  import Sawo from 'sawo'
  import { navigate } from 'gatsby'
  ```

- **Styling the JavaScript**:

```cpp

 // Styles
 const pageStyles = {
   color: '#bf7ed6',
   padding: 80,
   fontFamily: 'Roboto, sans-serif, serif',
 }
 const headingStyles = {
   marginTop: 10,
   marginBottom: 45,
   maxWidth: 400,
 }
 // markup
 const IndexPage = () => {
   useEffect(() => {
     var config = {
       // should be same as the id of the container created on 3rd step
       containerID: 'CONTAINER_ID_HERE',
       // can be one of 'email' or 'phone_number_sms'
       identifierType: 'email',
       // Add the API key copied from 5th step
       apiKey: 'API_KEY_HERE',
       // Add a callback here to handle the payload sent by sdk
       onSuccess: (payload) => {
       // you can use this payload for your purpose
         navigate('/TO_PAGE_HERE')
       },
     }
     let sawo = new Sawo(config)
     sawo.showForm()
   }, [])
   return (
     <main style={pageStyles}>
       <title> Login Page </title>
        <h1 style={headingStyles}>Login Page</h1>
        <div id="sawo-container" style={{ height: '300px', width: '400px' }}> </div>
     </main>
   )
 }
 export default IndexPage

```

Now Fill out these Placeholders:

| Placeholders | Solutions |
|-|-|
| `ID` | Fill the "Project ID" mentioned on your SAWO Dashboard.
| `API_KEY` | Fill the "API Key" mentioned on your SAWO Dashboard. 

Now Link your index.js and the Login Page

--- 

Now Link your index.js and the Login Page

## 3. Congratulations Your Project is ready:
      Project View:

<p align="center">
<img src="https://user-images.githubusercontent.com/77458628/143478732-a5ba1913-5bfc-4832-b21d-29c2189b5675.png" width="730" height="350">
</p>

---

## 4. Conclusion

"Congratulations!! You have successfully integrated SAWO API on your "Gatsby site".
 
Your SAWO API is now ready to be used in the Gatsby 

## What's Next?

🚀 Form Customisation and Design [here!](https://docs.sawolabs.com/sawo/quickguides/customisation)

🚀 Queries? Check the [FAQ Docs](https://docs.sawolabs.com/sawo/)

🚀 Share your Expereince Join our  [SAWO Discord community](https://discord.gg/mC7QKBTp)👨🏻‍💻👩🏻‍💻  for new and exciting opportunities.

🚀 New Project:  feel free to look at the [SAWO Documentation](https://docs.sawolabs.com/sawo/getting-started) , here you can find integration 
                 in React, Django and other frameworks.
                 

<h1 align="right"> Keep Learning 🎯 </h1>






