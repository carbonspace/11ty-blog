---
title: Create an NPM package
description: Creating and publishing a reusable NPM package
date: 2023-02-30
tags:
  - node.js
  - npm
  - github
  - sass
  - css
---

The public npm registry is a database of JavaScript packages, each comprised of software and metadata. Open source developers and developers at companies use the npm registry to contribute packages to the entire community or members of their organizations, and download packages to use in their own projects.

**To share your code publicly in a user or organization namespace**, you can [publish public user-scoped or organization-scoped packages to the npm registry](https://docs.npmjs.com/creating-and-publishing-scoped-public-packages).

## How to Create an NPM Package

### 1. Install Node  

If you do not already have Node installed, you'll need to install it for this project. [Download and Install Node.js](https://nodejs.org/en/download/)

Check your version of node.js

```sh
node --version 
# or
node -v
```

### 2. Initialize a Git Repository

Create a new project directory and navigate into it. Then, run the following to set up the necessary files and data structures that Git needs to start tracking changes in that directory.  

```sh
git init
```

Here's what `git init` does:

1. **Creates the .git directory:** The most important thing that `git init` does is create a hidden directory called `.git` in the root of your project directory. This directory is where Git stores all the configuration files, object database, and other data required to manage the version control of your project.

2. **Sets up default configuration:** `git init` also creates a basic configuration file within the `.git` directory, which contains default settings for the repository. This includes information like the repository's name and the email address associated with it.

3. **Initializes the main branch:** It initializes the main branch of your repository, which is usually called "main" by default. This branch is where you'll start making your initial commits.

After running git init, your project is set up as a Git repository, and you can start using Git to track changes, make commits, and collaborate with others. You can add files to the repository using git add, commit changes using git commit, and perform various other Git operations.

### 3. Initialize a Remote GitHub Repository

Make sure you create remote version of your repository on GitHub. This is where your source code will live and be distributed from.


### 4. Initialize NPM (or Yarn, pnpm) in Your Project

Navigate to the root directory of your project and run: 

```sh
npm init
#or
yarn
# or 
pnpm install
```

This command will create a `package.json` file. Follow the prompts to fill this out with your project details.


## 5. Add Your Code

Add the code for your package.

Create the file that will be loaded when your module is required by another application. For this example, it will be the `index.js` file.

Inside `index.js`, add the code for your new package.  
  ```sh
  //index.js

  function initPackage() {
    return "Initializing NPM Package"
  }

  module.exports = initPackage
  ```

After creating your function, export the function using `module.exports`. `module.exports` is a way to specify the values, functions, or objects that you want to make available for other modules to import and use. In this example, we'll be making the `initPackage` function available for import and use.

You should now have a basic package created. Before publishing, **make sure to test your package**. testing reduces the chance of publishing bugs to the NPM registry.

## How to Test  your NPM Package

Testing ensures that your NPM package works as expected. There are multiple ways to test your package.

### 1. Navigate to the `root` of your `package` project

Run: 

```sh
npm link
```

This makes your package available globally and you can require the package in a different project to test it out. 

Create a `test` folder. And inside that test folder, add a `script.js` file.

```sh
- [test]
  - script.js
```

Now add the package to the test folder.

```sh
npm link <package-name>
```

If our package name is `test-js-package`, we would run:

```sh
npm link test-js-package
```

This will create a `node-modules` directory and will add all the files and directories from your package.

You can now import (require) your package and use it for your test.

```sh
// test/script.js

const initPackage = require('test-js-package')

console.log(initPackage())
```

The `test-js-package` is expected to return the string `Initializing NPM Package`. Check the console output and you should see this string when running the script.

Once you have tested your package and ensured it works as expected, you can now publish it on the NPM registry.

## How to Publish Your NPM Package

[Login or signup to npm ](https://www.npmjs.com/)

After signing in, open your terminal, navigate to the root of your project and run:

```sh
npm login
```

Enter your `username` and `password` at the prompt and you should see a message like: 

`Logged in as <your-username> on https://registry.npmjs.org/.`

Publish your package on the NPM registry by running: 

```sh
npm publish
```

If published successfully, you'll get a message like: 

```sh
npm notice
npm notice test-js-package@1.0.0
npm notice === Tarball Contents ===
npm notice 20B README.md
npm notice 76B package.json
npm notice === Tarball Details ===
npm notice name: test-js-package
npm notice version:       1.0.0
npm notice filename:      test-js-package-1.0.0.ygz
npm notice package size:  484 B
npm notice unpacked size: 654 B
npm notice shasum:        XXXXXXXXXX
npm notice integrity:     XXXXXXXXXX 
npm notice total files:   3
npm notice
npm notice Publishing to https://registry.npmjs.org/
+ test-js-package@1.0.0
```

Congratulations! You just published your first NPM package. 

Visit the [NPM website](https://www.npmjs.com/) and run a search for your package. You should see your package show up in the search results. 

## How to Publish Scoped NPM Packages

If an existing package has the same name you would like to use for your package, the workaround is to publish a scoped package.

When you publish a scoped package, you have the option to make it public or private. If the package is private, you can choose who you want to share it with.

### Create a Scoped NPM Package

Navigate to the root of your project.

Run `npm init` and pass your `username` as the value to the `scope` flag.

`npm init --scope=@your-username`

Follow the prompts to create a `package.json` file. For your package name, the format should be `@your-username/package-name`

For example: `@carbonspace/test-js-package`

You can now add the code for your pacakge and test it. The process follows the same process above.

Then, publish your scoped package by running:

`npm publish --access public`

Change from `public` to `private` if you don't want to make the package available for public use.

When, published successfully, you should see a message like:

```sh
npm notice
npm notice Publishing to https://registry.npmjs.org/
+ @carbonspace/test-js-package@1.0.0
```

Congratulations! You've published your scoped package. You should see your scoped package on NPM if you search for it. 

Source: [How to Create and Publish an NPM Package – a Step-by-Step Guide](https://www.freecodecamp.org/news/how-to-create-and-publish-your-first-npm-package/)

***

## More Links

[Publishing my own CSS utility library on NPM](https://dev.to/evanwinter/create-your-own-css-utility-library-582d) -> [Project GitHub](https://github.com/evanwinter/styles)

[Create your own css npm module and use it in your project](https://medium.com/@jerrythimothy/create-your-css-npm-module-and-use-it-in-your-project-178894834f08)

[Creating my first npm package](https://www.csrhymes.com/2019/12/08/creating-my-first-npm-package.html)


