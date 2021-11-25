# Integrate SAWO in a NextJS Webpage

## What is NextJS?
* NextJS is an **Open-Source Development Framework** for building Server-side & Client-side rendered React applications, so that users can view and interact with..
* It performs 2 kinds of Rendering:
     1. Pre-rendered (For Static Generation (SSG)), and
     2. Server-Side rendering (SSR) are supported on a per-page basis
* It also performs **API Routing** that helps to access data present within the databases.
* NextJS acts as a complete full-stack framework, which is built on top of React.

# Software Requirements
  * [Node.js](https://nodejs.org/en/) (v14.15 or newer)
  * Operating System: MacOS, Windows (including WSL), and Linux.
  * [Visual Studio Code](https://code.visualstudio.com/#alt-downloads)

*Check the detailed Guide [here](https://nextjs.org/learn/basics/create-nextjs-app/setup)*


## Why use NextJS?
* It is a simple **Static Site Generators**
* It renders JavaScript in the browser itself
* The client-side application has full interactivity with the content, despite it effectively being just a copy-paste content.
* Cross-Platform
* Short Loading Times
* Supports TypeScript
* **Zero Configuration**: The Pages & Applications are automatically compiled, and bundled.


# Get Started
Let's start by:
## 0. Creating a NextJS Webpage
After all your installations; You will have something like this on the left of your code-area *[VSCode Explorer]*.

![1](https://user-images.githubusercontent.com/61507305/143485640-3eed7920-7873-4bc7-8abf-8fd7dd3259a7.PNG)


## 1. Generate a SAWO API key
   - Create / Register for an account with SAWO [here!](https://dev.sawolabs.com/) for passwordless authentication.
   - If you already have one, then navigate to **[SAWO Dashboard](https://dev.sawolabs.com/dash/dashboard)**.
   - On your SAWO dashboard, click on **Create New Project** button at the bottom left to create your new project.

<p align="center">
<img src="https://github.com/shreya-gb/Sawo-Docs/blob/main/Gatsby/SAWO.jpg" width="700" height="350">
</p>

   - Choose **Web** 💻 (because your building a webpage)
<p align="center">
<img src="https://user-images.githubusercontent.com/61507305/143178340-0e0e96ea-2b08-4839-9adf-bc6de42d0790.png" width="700" height="350">
</p>

   - Or, Choose your setup mode based on your preference.

 ## Code : For creating your custom webpage using *NextJS*.
 <p align="center">
 <img src="https://github.com/shreya-gb/Sawo-Docs/blob/main/Gatsby/Code.png" width="690" height="350">
 </p>

   - Click **Continue**.

   - Provide a name for your project that you intend to integrate it with. (Here's mine: ```SAWO_Login```)

<p align="center">
<img src="https://user-images.githubusercontent.com/61507305/143486121-9e990f0b-95f3-43c8-822c-9d9170b772f7.png" width="280" height="300">
</p>

  ## Host Name

| Property | Solution |
|-|-|
| `Not Deployed` | Your default **LOCAL HOSTNAME** itself will be your hostname: "**127.0.0.1**" 😎|
| `Deployed/Hosted` | Enter the **DOMAIN NAME** without the preceeding or trailing special symbols like the ```/``` or ```www```, ```http://```, ```https://```, ```ftp://```, and so on.|

  **Example:** https://dev.sawolabs.com/ should be kept as **dev.sawolabs.com**

- Finally, click the **CREATE** button!
- By default, you API Keys created using SAWO are downloaded as a `csv` file. Securely, save them.


<h1 align="center"> Wohoo!!🎊 You successfully generated an API Key for yourself! </h1>

---

## 2. Integrate SAWO within NextJS

- Assuming, you have created a new "Project" during your instalation process, that same "Project name must be remembered"



- **Follow this path**: <br />

{ Your Project name } ▶ Pages ▶ index.js [If, you are working using JavaScript]



- **Install SAWO-React SDK**(Package): Within your code terminal, before you integrate SAWO API in your project.

  ```shell
  npm i sawo-react
  ```


- Create a new *JavaScript* file, for keeping all your ***SAWO Login*** UI data in one place.


- **Import SawoLogin - SDK for React**: Import this class:

  ```js
  import SawoLogin from "sawo-react"
  ```


- **Import Classes**: Import these classes:

  ```js
  import React, { useEffect } from "react";
  import SawoLogin from "sawo-react";
  ```


- **Style the JavaScript Sheet**:
     1. Style in the same "Login - JavaScript file".
     2. Copy contents from the ```index.js``` boilerplate.
     3. Feel free to change the *style properties*, according to your convinience.
     4. You can create a login page using below code.


#### Copy and paste this code:
  ```js
    import React, { useEffect } from "react";
    import SawoLogin from "sawo-react";

     const [PAGE_NAME] = () => {
          function sawoLoginCallback(payload) {
     console.log(payload);
           }

      const sawoConfig = {
         onSuccess: sawoLoginCallback, //required,
         identifierType: "phone_number_sms", //required, must be one of: 'email', 'phone_number_sms',
         apiKey: "API_KEY_HERE", // required, get it from sawo dev.sawolabs.com,
         containerHeight: "300px", // the login container height, default is 300px
      };

      return (
      <div>
         <SawoLogin config={sawoConfig} />
      </div>
      );
      };
      
      export default [PAGE_NAME];
       ```


| Placeholders | Solutions |
|-|-|
| `API_KEY_HERE` | Enter the "API Key" mentioned on your SAWO Dashboard|
| `"PAGE_NAME"` | Enter the JavaScript file name in Camelcase (Abc)|


- **Update your index.js**:


  ```js
  import { useEffect } from 'react'

  export default function Home() {
    return (
        <div>
          <h1 align="center" width= {50} height= {50}> Hello! Welcome to your NextJS Dashboard! </h1>
        </div>
    )
  }
  ```


---

## 3. Final View


## Login with Phone
![Login](https://user-images.githubusercontent.com/61507305/143489308-cd19cc62-5446-46ba-baab-4c1ca441b397.png)

## Redirected Page
![Redirected](https://user-images.githubusercontent.com/61507305/143489302-a4b86b00-de8b-4205-8fe1-4d673dd9fead.png)


---

# Who uses NextJS?

#### Websites of Netflix, GitHub, Uber, Ticketmaster, Starbucks many other renowned companies use NextJS.

---

## 4. Conclusion

"Congratulations to you!! 🥇 On successfully integrating SAWO API on your "NextJS Webpage". Good to see you didn't give up halfway! 🎊


The SAWO API is now ready to be used in your NextJS Webpage 🤘


The Documentation of the NextJS integration will be up soon, on the SAWO Documentation.


## Not interested in reading the docs?


Check this [Tutorial](https://youtu.be/) here, that I have demonstrated from scratch to complete integration.


## Still stuck somewhere? Want to suggest a Feature?

Ask our community members at [SAWO](https://discord.com/invite/TpnCfMUE5P)👨🏻‍💻👩🏻‍💻 Join our Discord community 🎯

---

# What's Next?

🚀 **Up for a next project**: Integrate with the help of these [docs](https://docs.sawolabs.com/sawo/getting-started)!
There are various options among frameworks, or to create an app, and so on.

🚀 **Queries?** Check the [FAQ Docs](https://docs.sawolabs.com/sawo/)

🚀 **Interested in our community?** Join our [Discord](https://discord.com/invite/TpnCfMUE5P) community for new and exciting opportunities, & who knows might be lucky to work at SAWO LABS with your skills.


---
