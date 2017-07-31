# Introduction

### What is npm?

**npm** stands for **Node Package Manager** and helps with installation and management of packages in Node.js by providing a useful command line interface.

### What is a Node package?

A Node package is a library of code that implements a functionality. Naturally, developers want to import and use it within a project instead of re writing it.

### Where can i get the Node packages from?

Users open source and publish their packages in [npm Registry](https://www.npmjs.com/search). Since these packages are open and free, developers usually check README, stats and stars of each package in [GitHub](https://www.github.com) in order to decide how useful is a library before using it.

### Installing npm

npm is installed along with [NodeJS](https://nodejs.org/en/download/) installation. This link provides NodeJS binaries and installers.

Alternatively for linux users run the following command from terminal replacing the node version `setup_8.x`. This example is for node version 8.
```sh
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
```

# package.json

package.json file is created automatically from npm when initializing a project. It holds information for identifying and managing a project. It looks like that:
```js
{
  "name": "my_app",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "react": "^15.5.4"
  },
  "devDependencies": {
    "eslint": "^3.19.0",
   }
}
```

It holds the list of all dependencies and devDependencies packages. Dependencies are the modules needed to be installed for a project to run while devDependencies are the modules used by the developer to make his life easier. 

Versions of Node packages in package.json file follow the [semantic versioning rules](http://semver.org/). They can also contain the caret(^) or tilde(~) character in front of them. Caret instructs npm to install up to the latest available minor version, while tilde up to the latest available patch version.

When `npm install` runs all packages are installed from both "dependencies" and "devDependencies" sections.

# Commands

### Check version

**npm** version

```sh
npm -v
```

**node** version

```sh
node -v
```

### Initialialize project

Starts a process that will create **package.json** file in your current folder. While initializing a questionary command line will be initiated where at least **name** and **version** of the project should be provided.

```sh
npm init
```

### Installation

Install all project packages as listed in package.json file locally.

```sh
npm install
```

Install single package locally.

```sh
npm install <package_name>
```

Install single package globally. That bein said, packages installed that way be run from any path.

```sh
npm install <package_name> -g
```

### List packages

Print to stdout all project packages installed along with their respective versions, including their dependencies in a tree-structure.

```sh
npm list
```

Print to stdout only the dependencies of the first level. This command is usefull to check the versions of the packages installed locally.

```sh
npm list --depth=0
```

### Execute task automation scripts

npm supports the execution of scripts for task automation. npm comes with out of the box scripts and also allows developers to create custom ones.

Four [out of the box scripts](https://docs.npmjs.com/misc/scripts) come with project initialization and are executed as shown below:

```
npm start
npm test
npm build
npm install
```

Custom scripts are executed by adding the word `run` before the script name as shown below

```sh
npm run deploy
```

# Hands on examples

### Install a node package

As an example, we will install package [reqlog](https://www.npmjs.com/package/reqlog) from npm Registry. Follow the steps below to setup the package in your app.

1. Install package

Package reqlog will be installed installed under node_modules folder and its reference will de added in package.json.

```sh
npm install reqlog
```

2. Verify package was installed

Returns the list of packages with their version in folder node_modules.

```sh
npm list
```

Output should look like this:

```sh
my-app@1.0.0 C:\my-app
`-- reqlog@1.1.3
  `-- chalk@1.1.3
	+-- ansi-styles@2.2.1	
	+-- escape-string-regexp@1.0.5
	+-- has-ansi@2.0.0
	| `-- ansi-regex@2.1.1
	+-- strip-ansi@3.0.1
	| `-- ansi-regex@2.1.1 deduped
	`-- supports-color@2.0.0
```

3. Verify package was added in package.json

View package.json file.

```sh
cat package.json
```

Output should look like this:

```js
"dependencies": {
  "reqlog": "^1.1.3"
},
"devDependencies": {},
```
