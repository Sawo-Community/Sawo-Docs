# Passwordless Authentication in Nuxt.js with SAWO

Nuxt.js is a free and open source web application framework based on Vue.js, Node.js, Webpack and Babel.js. Nuxt is inspired by Next.js, which is a framework of similar purpose, based on React.js.

# Requirements

- [Node.js 15.5+](https://nodejs.org/en/) or later
- npm (comes bundled with node.js) or [yarn](https://yarnpkg.com/getting-started/install)
- A text editor ([VS Code](https://code.visualstudio.com/) is preferrable)

# Get Started

Once the requirements are satisfied, we can go ahead with further steps.

## 0. Create Next app

- Enter the following command in the terminal to create a Nuxt.js app.

  ```sh
  npm init nuxt-app <project-name>
  # or
  yarn create nuxt-app <project-name>
  ```

  You can select all default configurations or modify as per your requirement. Replace `<project-name>` with the name of your project. (eg: nuxt-auth)

- Now navigate into your project folder using cd command (change directory) and build it locally.

  ```sh
  cd <project-name>
  # cd next-auth
  yarn dev
  ```

- Create a container and give it an id. We'll use this id to display the SAWO form later.

  ```html
  <div class="formContainer" id="sawo-container" v-if="!isLoggedIn"></div>
  ```

- Now, let's style the container so that the form fits perfectly when loaded.
  ```html
  <style>
    #sawo-container {
      width: 400px;
      height: 400px;
    }
  </style>
  ```
  You can alternatively use the class selector `.formContainer` for styling instead of `#sawo-container`

## 1. Generate SAWO API key

- Navigate to SAWO Dashboard or create a new account [here](https://dev.sawolabs.com/) and log in.

- In the SAWO dashboard, click on the create project button at the bottom left to create a new project.
  ![Project Button](img/create-button.png)

- Choose web and then code since we're working with web framework and will be writing the custom code ourselves.

![Select Web](img/select-web.png)

Click continue. You'll see a similar prompt like the one below.
![Create Project](img/create-project.png)

- Name your project with a relevant name.
  2.1 For development in a local machine, the hostname should be set to 'localhost'.

  > If using "localhost" as hostname is not working for you, try "127.0.0.1"

  2.2 For production, the hostname should be set to your domain.

  > If you are adding your domain do not add 'https://', ''http://', 'www' or even trailing backslash. Example: https://dev.sawolabs.com/ should be kept as dev.sawolabs.com

On clicking the create button, we can successfully see the API key created prompt and SAWO keys csv file downloaded.

## 2. Installing SAWO Package

- Before we can use the SAWO API, we'll have to install the SAWO module. Use the following command in the nuxt js project folder to install the SAWO package.

  ```sh
  npm i sawo
  # or
  yarn add sawo
  ```

## 3. Implement Authentication in Next.js using SAWO

- Enter the import line below inside the script tag in the login page to import the sawo class. Here the login page refers to the file where we're planning to show the login form (say index.vue).

  ```js
  import Sawo from 'sawo'
  ```

- Now, let's store assign and store some values so that we can use them to modify the data displayed in our page.
  ```js
  data: () => ({
    isLoggedIn: false,
    currentTitle: "Login Page",
    userPayload: {},
    Sawo: null,
  }),
  ```
- Inside mounted, let's add our configuration for SAWO login form.

  ```js
  const config = {
    // should be same as the id of the container created on 3rd step
    containerID: 'CONTAINER_ID_HERE',
    // can be one of 'email' or 'phone_number_sms'
    identifierType: 'IDENTIFIER_HERE',
    // Add the API key copied from 5th step
    apiKey: 'API_KEY_HERE',
    // Add a callback here to handle the payload sent by sdk
    onSuccess: (payload) => {
      // you can use this payload for your purpose
      this.userPayload = payload
      this.isLoggedIn = true
      this.currentTitle = 'Dashboard'
    },
  }
  ```

  - Replace the 'CONTAINER_ID_HERE' with the id of your div.
  - Replace the 'IDENTIFIER_HERE' with either 'email' or 'phone_number_sms'
  - Replace 'API_KEY_HERE' with the api key from your sawo dashboard.
  - Finally, on successful payload, do your preferred action.

- Now, let's create an instance of the SAWO class

  ```js
  this.sawo = new Sawo(config)
  ```

- To show the form in the container, let's call the showForm method with the instance created

  ```js
  this.sawo.showForm()
  ```

- After combining all the above pieces of code, we get a similar code as below

  ```html
  <template>
    <div class="containerStyle">
      <section>
        <h2 class="title">{{ currentTitle }}</h2>
        <div class="loggedin" v-if="isLoggedIn">Hello User</div>
        <!-- The div in which sawo form is displayed -->
        <div class="formContainer" id="sawo-container" v-if="!isLoggedIn"></div>
      </section>
    </div>
  </template>
  ```

  ```html
  <script>
    import Sawo from 'sawo'
    export default {
      name: 'Sawo',
      data: () => ({
        isLoggedIn: false,
        currentTitle: 'Login Page',
        userPayload: {},
        Sawo: null,
      }),
      mounted() {
        const config = {
          // should be same as the id of the container
          containerID: 'sawo-container',
          // can be one of 'email' or 'phone_number_sms'
          identifierType: 'email',
          // Add the API key
          apiKey: 'ede9466f-697c-41c5-afb7-c054807f0975',
          // Add a callback here to handle the payload sent by sdk
          onSuccess: (payload) => {
            this.userPayload = payload
            this.isLoggedIn = true
            this.currentTitle = 'Dashboard'
            console.log('Payload : ' + JSON.stringify(payload))
          },
        }
        this.Sawo = new Sawo(config)
        this.Sawo.showForm()
      },
    }
  </script>
  ```

  ```html
  <style>
    #sawo-container {
      width: 400px;
      height: 400px;
    }
  </style>
  ```

- If you have followed the tutorial well, you'll see a login form similar to the one given below once the page is loaded.
  ![Login Page](img/login-page.png)

## 4. Conclusion

Congratulations! You have made it till the end and have learnt how to implement passwordless authentication in Nuxt.js with SAWO. In case you're facing difficulties, here's a [working demo](https://youtu.be/U4Dl-3yH_ME) of the tutorial you just went over. Find the source code for the same [here](https://github.com/irsayvid/sawo-mini/tree/main/nuxt-auth).

# What's Next?

Now that you've learnt how to authenticate in Next.js, feel free to look at the [SAWO documentation](https://docs.sawolabs.com/sawo/) for authentication in various web frameworks, mobile apps and no code platforms. Keep building :)

Made with :heart: by [Divya Sri Darimisetti](https://github.com/irsayvid)
