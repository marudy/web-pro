# Introduction

### What is npm?

[npm](https://docs.npmjs.com/getting-started/what-is-npm) stands for **Node Package Manager** and helps with installation and management of packages in [Node.js](https://nodejs.org/en/) by providing a useful command line interface.

### What is a Node package?

A Node package is a library of code that implements a functionality. Naturally, developers want to import and use it within a project instead of re writing it.

### Where can i get the Node packages from?

Developers open source and publish their packages in [npm Registry](https://www.npmjs.com/search). 

Since these packages are open and free, users are recommended to consult the Stats at the right of the web page of npm Registry for a package. For example see Stats of [lodash](https://www.npmjs.com/package/lodash) package. There is displayed the number of installments along with the GitHub link which provides the stars and README of each package in order to decide how useful is a library before using it.

### Installing npm

npm is installed along with [Node.js](https://nodejs.org/en/download/) installation. Use [nvm](https://github.com/marudy/web-pro/blob/web-pro-npm/tools/nvm/nvm-guide.md#install-a-new-version) to install Node.js.

```sh
nvm install <node-version>
```

# package.json

[package.json](https://docs.npmjs.com/files/package.json) file is created automatically from npm when initializing a project. It holds information for identifying and managing a project. It looks like that:
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

It holds the list of all [dependencies](https://docs.npmjs.com/files/package.json#dependencies) and [devDependencies](https://docs.npmjs.com/files/package.json#devdependencies) packages. Dependencies are the modules needed to be installed for a project to run while devDependencies are the modules used by the developer to make his life easier. 

Versions of Node packages in package.json file follow the [semantic versioning rules](http://semver.org/). They can also contain the caret(^) or tilde(~) character in front of them. [Caret](https://docs.npmjs.com/misc/semver#caret-ranges-123-025-004) instructs npm to install up to the latest available minor version, while [tilde](https://docs.npmjs.com/misc/semver#tilde-ranges-123-12-1) up to the latest available patch version.

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

For more details check npm documentation for [npm-version](https://docs.npmjs.com/cli/version)

### Initialialize project

Starts a process that will create **package.json** file in your current folder. While initializing a questionary command line will be initiated where at least **name** and **version** of the project should be provided.

```sh
npm init
```

For more details check npm documentation for [npm-init](https://docs.npmjs.com/cli/init)

### Installation

Install all project packages as listed in package.json file locally.

```sh
npm install
```

Install single package locally. From Node.js version 5 `--save` flag is a default option so no need to provide.

```sh
npm install <package_name>
```

Install package in devDependencies.

```sh
npm install <package_name> --save-dev
```

Install single package globally. That being said, packages installed to run from any path. [Global package](https://nodejs.org/en/blog/npm/npm-1-0-global-vs-local-installation/) are important, but should be avoided if not needed. Only utils packages should be installed globally.

```sh
npm install <package_name> -g
```

Install package specific version. For example, `npm install reqlog@1.1.2`

```sh
npm install <package_name>@<package_version>
```

For more details check npm documentation for [npm-install](https://docs.npmjs.com/cli/install)

### List packages

Print to stdout all project packages installed along with their respective versions, including their dependencies in a tree-structure.

```sh
npm list
```

Print to stdout only the dependencies of the first level of the tree-structure. This command is usefull to check the actual version of the packages installed locally in relation to the versions existing in package.json.

```sh
npm list --depth=0
```

For more details check npm documentation for [npm-ls](https://docs.npmjs.com/cli/ls)

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
