# Integrate Sawo in Gatsby

Gatsby is a free and open source static site generator for React. It combines the power of React with the simplicity of a static site. It is easy to use and supports a wide range of features. It uses GraphQL to power its data layer and webpack to bundle and optimize your code.

Gatsby has a large ecosystem of [plugins](https://www.gatsbyjs.com/plugins/) and [themes](https://www.gatsbyjs.com/docs/themes/) that make it easy to build a site with Gatsby.

# Requirements

These are the latest hardware and software requirements for Gatsby:

## Operating System

- macOS Sierra or later (10.12)
- Windows 10 ([setup instructions](https://www.gatsbyjs.com/docs/how-to/local-development/gatsby-on-windows/))
- Linux ([multiple distributions](https://www.gatsbyjs.com/docs/how-to/local-development/gatsby-on-linux/))

## Memory

As per the official documentation, Gatsby sites have been known to work from 500mb to 1GB of RAM.

## Software

### Node.js

LTS or higher version of Node.js, at the time of writing: Node.js 14.15.0 (LTS) or higher.

- Windows: Download the installer from [nodejs.org](https://nodejs.org/en/download/).
- macOS: Install Node.js from [Homebrew](https://brew.sh/).

  ```shell
  brew install node
  ```

- Linux: Install Node.js from [Ubuntu](https://www.ubuntu.com/download/desktop).

  ```shell
  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
  ```

  Add this to your `~/.bashrc` or `~/.zshrc` file:

  ```bash
  export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
  [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
  ```

  Then run the following commands:

  ```shell
  source ~/.bashrc

  nvm install node
  ```

### Package Manager

Choose your preferred package manager:

- NPM
- Yarn

NPM comes installed with Node, so you don't need to install it.

Yarn can be installed with NPM using the following command

```shell
npm install -g yarn
```

### Browser Support

Same as [React DOM](https://reactjs.org/docs/react-dom.html#browser-support), IE9+ (with polyfills) and popular modern browsers.

See more on [browser support](https://www.gatsbyjs.com/docs/how-to/custom-configuration/browser-support/).

# Get Started

Without further ado, let's get started.

## 0. Setup a Gatsby Project

If you haven't already, create a new Gatsby project using the Gatsby CLI.

```shell
gatsby new my-gatsby-project
```

To install gatsby cli globally, run the following command:

```shell
npm install -g gatsby-cli
```

## 1. Setup a Project on SAWO Dashboard

If you haven't already, register for a SAWO account [here](https://dev.sawolabs.com/)

Now create a new project on SAWO Dashboard by clicking on the "Create new Project" button.

![](../images/SAWO%201.png)

Select web as the platform and then code as the setup method and click on continue button in the bottom right corner.

![](../images/SAWO%2014.png)

Add a name for your project and a host name.

**Info on Host Name**: Host name is the name of the domain you want to use for your project but without http, www, or / at the end. For example, if you want to use `https://www.my-gatsby-project.com/`, your host name is `my-gatsby-project.com`. If your project is not gonna be deployed on a domain, and just be locally, write `127.0.0.1`.

Woohoo! You have successfully created a project on SAWO Dashboard and now you have API credentials to manage your project.

![](../images/SAWO%204.png)

## 2. Integrate Sawo in Gatsby

- Install SAWO SDK

  ```shell
  npm install sawo
  ```

- Import SAWO SDK

  ```js
  import Sawo from "sawo";
  ```

- A container has to be created for the SAWO component.

  ```jsx
  <div id="sawo-container" style={{height="300px", width="400px"}}></div>
  ```

- Write config for sawo

  ```js
  var config = {
    // should be same as the id of the container created on above
    containerID: "sawo-container",
    // can be one of 'email' or 'phone_number_sms'
    identifierType: "email",
    // Add the API key copied from 1st step
    apiKey: "",
    // Add a callback here to handle the payload sent by sdk
    onSuccess: (payload) => {},
  };
  ```

- Create a instance of sawo

  ```js
  var sawo = new Sawo(config);
  ```

- Render the SAWO component

  ```js
  sawo.showForm();
  ```

- The final code should be similar to

  ```jsx
  import * as React, { useEffect } from 'react'
  import Sawo from 'sawo'

  const IndexPage = () => {
    useEffect(() => {
        var config = {
          // should be same as the id of the container created on above
          containerID: "sawo-container",
          // can be one of 'email' or 'phone_number_sms'
          identifierType: "email",
          // Add the API key copied from 1st step
          apiKey: "",
          // Add a callback here to handle the payload sent by sdk
          onSuccess: (payload) => {},
        }

        let sawo = new Sawo(config)

        sawo.showForm()
    }, [])

    return (
      <main>
        <div id="sawo-container" style={{height="300px", width="400px"}}></div>
      </main>
    )
  }

  export default IndexPage
  ```

## 3. Conclusion

Congratulations! You have successfully integrated Sawo in your Gatsby project. Feel free to join [SAWO community](https://discord.gg/uV2NBNFmmw) and share your experience.

# What's Next?

Now that you have integrated Sawo in your Gatsby project, you can start building your site.

More awesome tech stacks that you can use with SAWO:

- [React](https://docs.sawolabs.com/sawo/single-page/react)
- [React Native](https://docs.sawolabs.com/sawo/react-native)
- [Django](https://docs.sawolabs.com/sawo/web-apps/django)
- [Flutter](https://docs.sawolabs.com/sawo/flutter)

