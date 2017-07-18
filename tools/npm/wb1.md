# Definition

### What is npm?
**npm** is the **node package manager** that makes it easy for JavaScript developers to share the code that they've created to solve particular problems, and for other developers to reuse that code in their own applications.

### Where can i find the node packages?
**npm** allows you to install node packages from [Registry](https://www.npmjs.com/package/request). These are open source packages. Since it is open source it is best practice to check the statistics before using the packages.

# Commands

### Installing and updating **npm**
**npm** is installed as part of the **node.js**

Check node version 
`node -v`

Check npm version
`npm -v`

Update npm if needed
`npm install npm@latest -g`

> **-g** flag: global install flag, the npm command can run from any path.

### Initialialize npm

A process will be started that will create package.json file
```sh
npm init
```

### Bring changes locally

Install the dependencies in the local node_modules folder
```sh
npm install
```

### Install a package

Install the package in the directory as a symlink in the current project. Its dependencies will be installed before it's linked.
```sh
npm install <folder>
```

Examples
```
npm install react-native-cli -g
npm install react-native --save
```
> **--save** flag: By default, NPM simply installs a package under node_modules. When you're trying to install dependencies for your app/module, you would need to first install them, and then add them (along with the appropriate version number) to the dependencies section of your package.json
* In node 5 **--save** flag is a default option.

### List packages
This command will print to stdout all the versions of packages that are installed, as well as their dependencies, in a tree-structure.
```sh
npm list
npm list --depth=0
```

# Scenarios

## Install a node package

Let's say that you want to install package [reqlog](https://www.npmjs.com/package/reqlog) from Registry and use it in your project. Here are listed the steps you need to do in order to make part of your project. In this example it is considered that npm is installed for your project.

1. Install package
> Run the following command
```sh
npm install reqlog
```
> Package is added in package.json
1. List the packages installed
> Run the following command
```sh
npm list
```
> Returns the list of packages in reqlog package. The path represents the dependancies, meaning that reqlog needs chalk package and so forth.
```sh
node_example@1.0.0 C:\node_example
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
