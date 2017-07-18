# Definition

### What is npm?
**npm** is the **node package manager** that makes it easy for JavaScript developers to share the code that they've created to solve particular problems, and for other developers to reuse that code in their own applications.

### Where can i find the node packages?
**npm** allows you to install node packages from [Registry](https://www.npmjs.com/package/request). These are open source packages. Since they are open source is best practice to check the statistics before using the packages.

# Commands

### Installing **npm**
**npm** is installed as part of the **node.js**

Check **node** version 
`node -v`

Check **npm** version
`npm -v`

### Initialialize npm

A process will be started that will create **package.json** file in your current folder. A questionary command line is initiated where at least **name** should be provided. **version** is always 1.0.0
```sh
npm init
```

A **package.json** file serves as documentation for what packages your project depends on. It also allows you to specify the versions of a package that your project can use using [semantic versioning rules](http://semver.org/).

### Install a package locally

Install the dependencies that kept in **package.json** in the local **node_modules** folder.
```sh
npm install
```

A package can be downloaded with the command
```sh
npm install <package_name>
```
This will create the **node_modules** directory in your current directory(if one doesn't exist yet), and will download the package to that directory.

Examples
```
npm install react-native-cli -g
npm install react-native --save
```
> **-g** flag: global install flag, if used **npm** can run from any path
> **--save** flag: By default, **npm** simply installs a package under node_modules. When you're trying to install dependencies for your app/module, you would need to first install them, and then add them (along with the appropriate version number) to the dependencies section of your package.json
* In node 5 **--save** flag is a default option

### List packages
This command will print to stdout all the versions of packages that are installed, as well as their dependencies, in a tree-structure.
```sh
npm list
npm list --depth=0
```

# Scenarios

## Install a node package

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
Returns the list of packages in **reqlog** package. The path represents the dependancies, meaning that **reqlog** needs **chalk** package and so forth.
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
