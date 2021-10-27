# Sawo-Docs

This repository contains all the documentations of the SAWO SDK. 

If you have any questions, join the [official discord server](https://discord.com/invite/TpnCfMUE5P). You will be able to ask your queries to the SAWO Team and our engineers will help you out.

# Table of Contents

* [Contributing](#contributing)
     * [Getting Started](#getting-started)
     * [Editing](#editing)
     * [Creating Pull Requests](#creating-pull-requests)
     * [Commenting on Pull Requests](#commenting-on-pull-requests)
     * [Reviewing Pull Requests](#reviewing-pull-requests)
* [Building and Validating](#building-and-validating)

## Contributing

### Getting Started

You can edit or create SAWO documentation directly in GitHub or by downloading the repo onto your machine and using an editor such as VS-Code.

### Editing

The quickest way to begin is editing directly on GitHub on your fork of the SAWO docs repo. Click the **Edit** icon on the top right corner of the page you want to edit in the SAWO documentation.

If this is the first time you're contributing, follow these steps: 
1. Select **Fork** in the top-right corner of the GitHub page to fork the repository.
2. Navigate to file you want to edit and select the Pencil icon (**Edit the file**) to open the editing interface.

### Creating Pull Requests

1. When you're ready to submit your changes, add a descriptive title and comments to summarize the changes made.
2. Select **Create a new branch for this commit and start a pull request**.
3. Check the **Propose file change** button.
4. Scroll down to compare changes with the original document.
5. Select **Create pull request**. 

### Commenting on Pull Requests

Once a pull request is submitted, multiple committers may comment on it and provide edits or suggestions which you can commit directly. You can also add line comments. Take a look at [Commenting on pull requests](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/commenting-on-a-pull-request) for more details.

### Reviewing Pull Requests

Once a pull request has been submitted and the correct label assigned, the review process begins. This includes aligning the content with the Style Guide, validating processes, and tagging any other relevant committers.

Once the review process is complete and depending on the type of issue it is (e.g., a typo fix vs. a new feature), the change is either merged into master and pushed immediately or merged into the release branch and pushed in alignment with the release. The branch is then deleted. 

## Building and Validating

If you've downloaded the repository and are editing SAWO documentation on your local machine, you can generate the HTML files from markdown. You can review your changes before you commit them or create pull requests.

**Note:** Commands can be executed on Linux, Mac, and Windows (using Powershell).

1. Open a terminal window, then clone a forked copy of the documentation repository by running the following command::
```sh
https://github.com/Sawo-Community/Sawo-Docs.git
```
2. Install [pipenv](https://docs.pipenv.org/) by using one of the following commands based on your operating system:

For Mac users where Homebrew is installed:
```sh
brew install pipenv  
```
For other operating systems
```python
pip install pipenv 
```

