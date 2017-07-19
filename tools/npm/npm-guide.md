# Definition

### What is npm?

**npm** stands for **Node Package Manager** and helps developers to install and manage the tools (or packages) in Node.js by providing a useful command line interface.

### What is a Node package?

A Node package is a library of code that implements a functionality and developers want to import and use within a project.

### Where can i get the Node packages from?

Users open source and publish their packages in [npm Registry](https://www.npmjs.com/search). Since these packages are open source and free developers usually check README, stats and stars of each package in [GitHub](https://www.github.com) in order to understand how useful is a library before using it.

### Installing npm

npm is installed along with [NodeJS](https://www.nodejs.com/) installation

# package.json

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

```sh
npm init
```
Starts a process that will create **package.json** file in your current folder. While initializing a questionary command line will be initiated where at least **name** and **version** of the project should be provided.

### Installation

Install [all project packages](#example-b) as listed in package.json file.

```sh
npm install
```

Install single package

```sh
npm install <package_name>
```

### List packages

Print to stdout all project packages installed along with their respective versions, including their dependencies in a tree-structure.
```sh
npm list
```

Print to stdout only the dependencies the first level. This command is usefull to check the installed versions of the packages.

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

Let's say that you want to install package [reqlog](https://www.npmjs.com/package/reqlog) from Registry and use it in your app. Listed below the steps you need in order to include package in your app. In this example it is considered that **npm** is installed your your app.

1. Install package

```sh
npm install reqlog
```

Package is installed under **node_modules** and is linked in **package.json**

2. List the packages installed

```sh
npm list
```

Returns the list of packages in **reqlog** package. The path represents the dependancies, meaning that **reqlog** **package.json** has as a dependancy **chalk**. Accordingly **chalk** **package.json** has as a dependancy **ansi-styles**, **escape-string-regex** and so forth.

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
