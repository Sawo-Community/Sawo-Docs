# Integrate SAWO in a Gatsby Site

## What is Gatsby?
* Gatsby is an ***open source framework*** that helps you to develop static webpages and apps with React.
* Gatsby sites are incredibly fast to build, and are equally quick in performance.

# Software Requirements
  * [Node.js](https://nodejs.org/en/) (v14.15 or newer) 
  * [Git](https://www.atlassian.com/git/tutorials/install-git)
  * Gatsby command line interface (CLI) (v3 or newer)
  * [Visual Studio Code](https://code.visualstudio.com/#alt-downloads)

*Check the detailed Guide [here](https://www.gatsbyjs.com/docs/tutorial/part-0/)*


## Why use Gatsby?
* If you love plugins, then you definitely will love their impressive collection of plugins.
* Build a Progressive Web App.


# Get Started
Let's start by:
## 0. Creating a Gatsby site
Create your first Gatsby site taking reference from the official [documentation](https://www.gatsbyjs.com/docs/quick-start/) of Gatsby.

## 1. Generate a SAWO API key
   - Create / Register for an account with SAWO [here!](https://dev.sawolabs.com/) for passwordless authentication.
   - If you already have one, then navigate to **[SAWO Dashboard](https://dev.sawolabs.com/dash/dashboard)** (if, already have one)
   - On your SAWO dashboard, click on **Create New Project** button at the bottom left to create your new project.

<p align="center">
<img src="https://github.com/shreya-gb/Sawo-Docs/blob/main/Gatsby/SAWO.jpg" width="700" height="350">
</p>

   - Choose **Web** 💻 (as your building a webpage)
<p align="center">
<img src="https://user-images.githubusercontent.com/61507305/143178340-0e0e96ea-2b08-4839-9adf-bc6de42d0790.png" width="700" height="350">
</p>

   - Choose your setup mode based on your preference.

 ## Code : For creating your custom web-app using *Gatsby*.
 <p align="center">
 <img src="https://github.com/shreya-gb/Sawo-Docs/blob/main/Gatsby/Code.png" width="690" height="350">
 </p>
   
 ## WordPress : If you want to integrate for no-code platform.
<p align="center">
<img src="https://github.com/shreya-gb/Sawo-Docs/blob/main/Gatsby/WordPress.png" width="700" height="350">
</p>

   - Click **Continue**.

   - Provide a name for your project that you intend to integrate it with. (Here's mine: ```myGatsby_Site```)

<p align="center">
<img src="https://user-images.githubusercontent.com/61507305/143178630-dd37512d-5b8f-423d-89f5-fc97f1b210ba.png" width="730" height="330">
</p>
 
  ## Host Name
  
| | |
|-|-|
| `Not Deployed` | Your default **LOCAL HOSTNAME** itself will be your hostname: "**127.0.0.1**" 😎|
| `Deployed/Hosted` | Enter the **DOMAIN NAME** without the preceeding or trailing special symbols like the ```/``` or ```www```, ```http://```, ```https://```, ```ftp://```, and so on.|

  **Example:** https://dev.sawolabs.com/ should be kept as **dev.sawolabs.com**

- Finally, click the **CREATE** button! By default, you API Keys created using SAWO are downloaded as a `csv` file. Securely save them.


<h1 align="center"> Wohoo!!🎊 You successfully set you an API Key for yourself. </h1>

---

## 2. Integrate SAWO in Gatsby


**Check your Parent Directory**: It must be *Gatsby site directory*.


- **Install SAWO SDK**(Package): Within your code terminal, before you integrate SAWO API in your project.

  ```shell
  npm i sawo
  ```


- **Import SAWO SDK**: After installation, create a new *JavaScript* file, for keeping your ***SAWO Login*** UI data in one place.

  ```js
  import Sawo from 'sawo'
  ```


- **Import Classes**: You can create a login page using below code. Import these classes:

  ```js
  import React, { useEffect } from 'react'
  import Sawo from 'sawo'
  import { navigate } from 'gatsby'
  ```


- **Style the JavaScript Sheet**: Style in the same "Login - JavaScript file". Copy contents from the ```index.js``` boilerplate.


#### Keep just this section within the boilerplate:
  ```js
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

<p align="center">
<img src="https://user-images.githubusercontent.com/61507305/143194253-db95a1a2-b598-4b93-ad46-742ca752aa25.png" width="730" height="350">
</p>


| | |
|-|-|
| `CONTAINER_ID_HERE` | Enter the "Project ID" mentioned on your SAWO Dashboard. Refer the image for reference (Yellow)|
| `API_KEY_HERE` | Enter the "API Key" mentioned on your SAWO Dashboard. Refer the image for reference (Green)|
| `/TO_PAGE_HERE` | Linking your index.js and the Login Page (with the directory path)|

---

## 3. Final View


<p align="center">
<img src="https://user-images.githubusercontent.com/61507305/143195937-423e0004-a29a-46db-999c-ace77025a95e.png" width="730" height="350">
</p>


---

# Who uses Gatsby?

#### Websites of Daniel Wellington, Headspace, Clubhouse and many other renowned companies use Gatsby.

---

## 4. Conclusion

"Congratulations to you!! 🥇 On successfully integrating SAWO API on your "Gatsby site". Good to see you didn't give up halfway! 🎊


The SAWO API is now ready to be used in your Gatsby site 🤘


The Documentation of the Gatsby integration will be up soon, on the SAWO Documentation.


## Not interested in reading the docs?


Check this [Tutorial](https://youtu.be/Vvl3WwVr5tg) here, that our fellow community member has demonstrated from scratch to complete integration.


## Still stuck somewhere? Want to suggest a Feature?

Ask our community members at [SAWO](https://discord.com/invite/TpnCfMUE5P)👨🏻‍💻👩🏻‍💻 Join our Discord community 🎯

---

# What's Next?

🚀 **Up for a next project**: Integrate with the help of these [docs](https://docs.sawolabs.com/sawo/getting-started)!
There are various options among frameworks, or to create an app, and so on.

🚀 **Queries?** Check the [FAQ Docs](https://docs.sawolabs.com/sawo/)

🚀 **Interested in our community?** Join our [Discord](https://discord.com/invite/TpnCfMUE5P) community for new and exciting opportunities, & who knows might be lucky to work at SAWO LABS with your skills.


---

# My References (Optional)

- [x] https://www.gatsbyjs.com/docs/tutorial/part-0/
- [x] https://www.mediacurrent.com/blog/what-is-gatsbyjs.n
- [x] https://github.com/auth0/nextjs-auth0#installation
- [x] https://docs.sawolabs.com/sawo/


<h1 align="right"> Keep Building, Learning & Networking 🎉 </h1>
