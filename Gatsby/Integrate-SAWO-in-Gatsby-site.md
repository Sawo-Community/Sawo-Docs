# Integrate SAWO in a Gatsby Site

Gatsby is a React-based open-source framework for creating websites and apps. It combines the control and scalability of dynamically rendered sites with the speed of static-site generation that helps developers build blazing fast websites and apps.

# Let's get our Gatsby site running with SAWO

To get our site running, we need to have a few things installed.

## Requirements

Node [Version 14.5+ ], Node Package Manager (NPM) [Version 6.x+]

### Creating a Gatsby site

Refer to the official [documentation](https://www.gatsbyjs.com/docs/quick-start/) of Gatsby to create your first Gatsby site.

### Generate SAWO API key

1. Navigate to SAWO Dashboard if you have an account or create a new account [here](https://dev.sawolabs.com/) by logging in.

2. In your SAWO dashboard, click on the create project button at the bottom left to create a new project.
   ![Project Button](img/create-button.png)

3. Choose web and then code since we'll be using react framework Gatsby and writing the custom code ourselves.

![Select Web](img/select-web.png)

Click continue. You'll be see a similar prompt like the one below.
![Create Project](img/create-project.png)

4. Name your project with relevant name. I've named it 'gatsbysite'. For development in a local machine, the hostname should be set to 'localhost'.

On clicking create button, you can successfully see the API key and SAWO keys downloaded.

### Integrating Gatsby site with SAWO

1. Before we can use SAWO API, we'll have to install the SAWO Package. Enter the following command in your terminal. (Make sure you're inside your Gatsby site folder)

   ```shell
   npm i sawo
   ```

2. Open your preferred page for login and enter the import line below to import sawo class.

   ```js
   import Sawo from 'sawo'
   ```

3. You can create a page using below code.

   ```
   import React, { useEffect } from 'react'
   import Sawo from 'sawo'
   import { navigate } from 'gatsby'
   ```

   ```
   // styles
   const pageStyles = {
   color: '#232129',
   padding: 96,
   fontFamily: '-apple-system, Roboto, sans-serif, serif',
   }
   const headingStyles = {
   marginTop: 0,
   marginBottom: 64,
   maxWidth: 320,
   }
   ```

   ```
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
   <title>Login Page</title>
   <h1 style={headingStyles}>Login Page</h1>
   <div
   id="sawo-container"
   style={{ height: '300px', width: '400px' }} ></div>
   </main>
   )
   }

   export default IndexPage

   ```

4. Replace the 'CONTAINER_ID_HERE' with the id of your div. In the above code it is 'sawo-container'.

5. Replace 'API_KEY_HERE' with the api key from sawo dashboard. Make sure to enquote it.

6. Finally, on successful payload, do your preferred action. In this case, I'm redirecting to new page.

Congratulations! You have successfully integrated SAWO with your Gatsby Site.

You can also check out the [Gatsby sample code on Github](https://github.com/irsayvid/gatsby-sawo).

## Conclusion

Voila! You've integrated SAWO succesfully in your Gatsby site.
Enjoy with SAWO and we will see you next time.
