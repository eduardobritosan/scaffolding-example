# Scaffolding class example

## Create a development environment

After confirming that Node.js is installed in our development machine, we create the basic directory structure of an empty dist folder, an empty build folder, a src folder with three subfolders, assets, css, js, and an index.html. This can easily be done through the following terminal command

```
mdkir -p dsi-p1-parcel-eduardobritosan/src/{css,js,assets}
```

## Initialize Git and NPM and add node_modules to .gitignore

Following the last step, we'll initialize Git with the usual commands
```
git init
git remote add origin repo-url
```

After that, we'll create the .gitignore and the README.md. 

Having finished the starting Git configurations, our next step is initializing NPM. We'll do that through

```
npm init -y
```

## Install Parcel. Globally or in the project? If project based, what should be taken into account?

We'll install Parcel globally. The reason for this is that we'll use it future projects and it's inclusion is not necessary in the package JSON for deployment purposes. If we had installed it in the project, we'd have to use npx in order to run parcel or any of its utilities.

```
npm install -g parcel-bundler
```

## Create the following NPM scripts: dev, build, deploy

We decided not to create a deploy script, rather, append the deploy to the build in order to have a constantly updating live deployment.

```
    "dev": "parcel src/index.html --port 8080",
    "clean": "rm -rf dist package-lock.json node_modules",
    "build": "parcel build src/index.html --no-source-maps --detailed-report --public-url /dsi-p1-parcel-eduardobritosan/ -d build && gh-pages -d build -o assignment"
```

## Install ESLint and Prettier

For the ESLint part, we installed it following the class's recomendation, that, while a bit stricter than usual, will allow us to be able to check for inconsistencies in our code and make it more legible. We also modified the eslintrc.json file to adapt it to our necessities.

```
{
    "env": {
        "browser": true,
        "es6": true
    },
    "extends": [
        "standard", "prettier"
    ],
    "plugins": [
        "prettier"
    ],
    "globals": {
        "Atomics": "readonly",
        "SharedArrayBuffer": "readonly"
    },
    "parserOptions": {
        "ecmaVersion": 2018,
        "sourceType": "module"
    },
    "rules": {
        "indent": ["error", 2],
        "semi": ["error", "always"]
    }
}
```

We followed the same process with Prettier, in this case creating our own .prettierrc file.

```
{
    "semi": true,
    "singleQuote": true,
    "tabWidth": 3,
    "useTabs": false
}
```