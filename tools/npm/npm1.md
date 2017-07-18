# Definition

### What is npm?
**npm** is the **node package manager** that makes it easy for JavaScript developers to share the code that they've created to solve particular problems, and for other developers to reuse that code in their own applications.

### What are node package?
Node package is a package (source code) that implements a functionality and can be imported and used in a project.

### Where can i find the node packages?
**npm** allows you to install node packages from [Registry](https://www.npmjs.com/). These are open source packages. Since they are open source is best practice to check the **Stats** and **stars** in **GitHub** before using them.

# Commands

### Installing **npm**
**npm** is installed as part of the **node.js**

Check **node** version 
```sh
node -v
```

Check **npm** version
```sh
npm -v
```

### Initialialize npm

A process will be started that will create **package.json** file in your current folder. A questionary command line is initiated where at least **name** and **version** should be provided.
```sh
npm init
```

A **package.json** file serves as documentation for what packages your project depends on. It also allows you to specify the versions of a package that your project can use using [semantic versioning rules](http://semver.org/).

### Install a package locally

Install the **dependencies** and **devDependencies** dev read from **package.json** in the local **node_modules** folder.
```sh
npm install
```

In Production there is a flag that installs only **dependencies**.
```sh
npm install -production
```

A package can be downloaded with the command
```sh
npm install <package_name>
```
This will create the **node_modules** directory in your current directory(if one doesn't exist yet), and will download the package to that directory.

##### Example A
```sh
npm install react-native-cli -g
```
**npm** will install package **react-native-cli** as a computer program. The package is stored in a global path on your system.
> **-g** flag: global install flag, if used **react-native-cli** package can run from any path

##### Example B
```sh
npm install react --save
```
**npm** will install package **react-native** in your current folder.
> **--save** flag: By default, **npm** simply installs a package under **node_modules**. When you're trying to install dependencies for your app/module, you would need to first install them, and then add them (along with the appropriate version number) to the **dependencies** section of your **package.json**
```sh
"dependencies": {
  "react": "^15.5.4",
  "react-dom": "^15.5.4"
},
```

Apart from **dependencies** section in **package.json** there are also **devDependencies** section. In general in **dependencies** are added packages that needed for the app to run while in **devDependencies** those that are needed mostly for development phase. For example **ESLint** is only to assist developer write more consistent code.
```sh
npm install eslint --save-dev
```
```sh
"devDependencies": {
  "eslint": "^3.19.0",
},
```

* Caret(^) in versioning means that **npm** will install all new **minor** and **patch** versions. So you can end up having installed **ESLint** version 3.20.0 while in **package.json** you will have 3.19.0 which is allowed. Changes on **major** versioning are not allowed.

* Tilde(~) in versioning means that **npm** will install all new **patch** versions. Changes on **major** and **minor** versioning are not allowed.

* In node 5 **--save** flag is a default option

### List packages

This command will print to stdout all the versions of packages that are installed, as well as their dependencies, in a tree-structure.
```sh
npm list
```

This command will print to stdout only the dependancies that are in the first level. This command is usefull to check the **installed version** of the packages versus the one in **package.json**.
```sh
npm list --depth=0
```

### Run scripts with npm

**npm** supports the "scripts" property of the **package.json** file. Scripts are usefull because they reduce complexity.

In the follwoing example **npm run deploy** command can be used to deploy app instaed of command line **git push dokku@192.168.11.168:carbon-website master -f**
```sh
"scripts": {
    "build": "jekyll build",
    "deploy": "git push dokku@192.168.11.168:carbon-website master -f",
    "preinstall": "sudo gem install jekyll",
    "start": "gulp",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

Standard scripts supported by **npm** can be used found [npm scripts](https://docs.npmjs.com/misc/scripts) and run as
```sh
npm start
npm test
npm build
npm install
```

Custom scripts run as
```sh
npm run deploy
```

# Scenarios

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
