# Integrate SAWO in a Gatsby Site

## What is Gatsby?
* Gatsby is an ***open source framework*** that helps you to develop static webpages and apps with React.
* Gatsby sites are incredibly fast to build, and are equally quick in performance.

# Requirements
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
   - Navigate to **[SAWO Dashboard](https://dev.sawolabs.com/dash/dashboard)** (if created an account) or Register for a new account [here!](https://dev.sawolabs.com/) without any password :)
   - On your SAWO dashboard, click on **Create New Project** button at the bottom left to create a new project. <img src="https://github.com/shreya-gb/Sawo-Docs/blob/main/Gatsby/SAWO.jpg" width="730" height="360">
   - Choose **Web** 💻
      - Select **code** as you wil be using *Gatsby* for a creating custom webapp. <img src="https://github.com/shreya-gb/Sawo-Docs/blob/main/Gatsby/Code.png" width="730" height="360">
      - Select **WordPress** for no-code integration & follow the instructions as mentioned. <img src="https://github.com/shreya-gb/Sawo-Docs/blob/main/Gatsby/WordPress.png" width="730" height="360">
      - Click **Contiinue**, where you would have a dashboard, with a unique set of credentials. <img src="https://github.com/shreya-gb/Sawo-Docs/blob/main/Gatsby/SAWO.jpg" width="730" height="360">
      - Type-in an appropriate conventional name for project that you intend to integrate it with. Assuming mine here, to be 'Web_Gate'.

---

### Not deployed/hosted; Default Hostname: 'localhost'
- In this case, Your default *local* hostname is "**127.0.0.1**"


### Deployed/hosted on a certain platform, Hostname: Set according to your domain.
- When entering your domain hostname; Enter just the **website link** without preceeding or trailing special symbols like the '/' or the 'www', 'http://', ''https://', 'ftp://', and so on.

> Sample: https://google.com/ should be just as ***google.com***

- Now, click the **CREATE** button!

# Wohoo!!🎊 You successfully set you an API Key for yourself.

- Check your API key created using SAWO, by downloading, and securely saving the `csv` file.

---

## 2. Integrate SAWO in Gatsby

- First, install the SAWO SDK(Package), before you integrate SAWO API in your project.
- Check your parent directory must be ***Gatsby site directory***.
- Enter this command within your code terminal.

  ```shell
  npm i sawo
  ```


- Create a JavaScript file, for keeping all your ***Login / Sign-Up*** UI data in one place. Then, type the below command to `import sawo class`.

  ```js
  import Sawo from 'sawo'
  ```


- You can create a login page using below code.

  ```js
  import React, { useEffect } from 'react'
  import Sawo from 'sawo'
  import { navigate } from 'gatsby'
  ```

  ```js
  // Stylesheet
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


## Who uses Gatsby?
#### Websites of Daniel Wellington, Headspace, Clubhouse and many other renowned companies use Gatsby.


## References
- [x] https://www.gatsbyjs.com/docs/tutorial/part-0/
- [x] https://www.mediacurrent.com/blog/what-is-gatsbyjs.n
- [x] https://github.com/auth0/nextjs-auth0#installation
