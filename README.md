# Setup a monorepo with Lerna

To setup a monorepo with Lerna + NPM, first initial the repo.

```
$ npm i -D lerna
$ npx lerna init
```

This will create a lerna.json configuration file as well as a packages folder, folder should now look like this:

```
lerna_monorepo/
    node_modules/
    packages/
    package.js
    lerna.json
```

In ./packages, I created 2 packages: React App & Nodejs+Express:

1. React app

```
$ npx create-react-app web-client
```

2. NodeJS + Express:

```
$ mkdir server-api
$ cd server-api
$ npm init -y
$ npm i express --save
```

With 'clean', Lerna remove the node_modules from the server-api and web-client:

```
$ npx lerna clean -y
```

With 'bootstrap', Lerna downloads dependencies with NPM and links the packages:

```
$ npx lerna bootstrap --hoist
```

Run the test for all packages:

```
$ npm run test
```

Run both packages: reactapp and express:

```
$ npm run start
```

Push the updates to the repository:

```
$ git add lerna.json package.json packages
$ git commit -m "install lerna, ready to publish"
```

Publish the new version to NPM:

```
$ lerna version
$ lerna publish from-git
```

Lerna can detect when a package has change:

```
$ lerna changed
```
