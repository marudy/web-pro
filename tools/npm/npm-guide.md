# Introduction

### What is npm?

**npm** stands for **Node Package Manager** and helps developers to install and manage the tools (or packages) in Node.js by providing a useful command line interface.

### What is a Node package?

A Node package is a library of code that implements a functionality and developers want to import and use within a project.

### Where can i get the Node packages from?

Users open source and publish their packages in [npm Registry](https://www.npmjs.com/search). Since these packages are open source and free, developers usually check README, stats and stars of each package in [GitHub](https://www.github.com) in order to understand how useful is a library before using it.

### Installing npm

npm is installed along with [NodeJS](https://www.nodejs.org/) installation

# package.json

All Node packages contain package.json file in the project root. This file is used to give information to npm that allows it to identify and manage a project. Information is maintained by npm in various metadata relevant to the project.

package.json sample:
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
  "devDependencies": {}
}
```

It contains the list of all dependencies needed for a project to run. When `npm install` runs npm will install all the packages listed in "dependencies" and "devDependencies" section. "devDependencies" section includes packages that needed mostly for development phase.

It also contains the versions of Node packages that a project uses according to [semantic versioning rules](http://semver.org/).

* Caret(^) in versioning means that npm will install all new *minor* and *patch* versions. Changes on *major* versioning are not allowed.

* Tilde(~) in versioning means that npm will install all new *patch* versions. Changes on *major* and *minor* versioning are not allowed.

# Commands

### Check tool version

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

Install [all project packages](#example-b) as listed in package.json file.

```sh
npm install
```

Install single package locally.

```sh
npm install <package_name>
```

Install single package globally. npm will install package `react-native-cli` as a computer program and can be run from any path.

```sh
npm install <package_name> -g
```

### List packages

Print to stdout all project packages installed along with their respective versions, including their dependencies in a tree-structure.
```sh
npm list
```

Print to stdout only the dependencies of the first level. This command is usefull to check the locally installed versions of the packages.

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

As an example, we install package [reqlog](https://www.npmjs.com/package/reqlog) from Registry. Follow the steps below to include package in your app. In this example it is considered that `npm install` already run for your app.

1. Install package

With this command package reqlog is installed under folder node_modules and is added in file package.json.

```sh
npm install reqlog
```

2. Verify package was installed

Returns the list of packages with their version in folder node_modules.

```sh
npm list
```

The tree path represents the dependancies, meaning that reqlog package.json file has as dependancy chalk package. Accordingly chalk package.json file has as dependancy ansi-styles, escape-string-regex packages and so forth.

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

Package added in "dependencies".

```js
"dependencies": {
  "reqlog": "^1.1.3"
},
"devDependencies": {},
```
