# NodeBits
NodeBits aims to provide you with an easy way to get a site up and running quickly. Since every site has different goals, requirements, and tech - NodeBits is built as a series a pluggable 'bits' that you can quickly combine into a powerful foundation for your site.

## Getting Started
The NodeBits package itself is the boot loader. You supply it with the bits and it puts them together. Each bit is intentionally focused on subset of the whole. To cut down on dependency bloat, each bit is distributed as an independent npm package - you only include what you need.

### Install
I recommend reading through the list of existing bits, choosing your combination and then installing them together.

For example:
```
npm install node-bits node-bits-express node-bits-code --save
```

or

```
yarn add node-bits node-bits-express node-bits-code
```

### Configuration
Each bit has their own configuration, for example, you may provide a path to the code bit or a connection string to a database bit.

These bits are then provided to the boot loader like:

```
import nodeBits from 'node-bits';
import nodeBitsExpress from 'node-bits-express';
import nodeBitsCode from 'node-bits-code';
import nodeBitsRest from 'node-bits-rest';

nodeBits([
  nodeBitsExpress({
    port: 4000,
  }),
  nodeBitsCode({
    path: `${__dirname}`,
  }),
  nodeBitsRest({
    prefix: 'api',
  }),
]);
```

## What is a "bit"
A bit is a building block of an app. Below are the existing bits I know about, but you can easily make your own. Each bit is given an opportunity to do something in the following hooks:

* initializeDatabase
* loadSchema
* loadRoutes
* initializeServer

## Current Bits
### [NodeBits-Express](https://github.com/jgretz/node-bits-express)
The express bit wraps the popular express package for hosting web apps. It will take all routes defined by other bits and configure express to listen for those routes. In addition, it also exposes easy hooks for you to provide custom configurations.

Visit the [repo](https://github.com/jgretz/node-bits-express) to find out more specifics.

### [NodeBits-Code](https://github.com/jgretz/node-bits-code)
The code bit allows you to use friendly code to express your schemas and routes. Rather than force you to use a DSL made up by a server or database package, this bit abstracts the concepts of routes and schema to their generic forms, which keeps your code nice, clean and straight forward while reducing complexity and coupling. It also follows the convention of the your folder structure so you can focus on adding value not configuring the server.

Visit the [repo](https://github.com/jgretz/node-bits-code) to find out more specifics.

### [NodeBits-Rest](https://github.com/jgretz/node-bits-rest)
The rest bit builds and exposes rest services for every schema object defined by bits during loadSchema.

Visit the [repo](https://github.com/jgretz/node-bits-rest) to find out more specifics.

### [NodeBits-Mongo](https://github.com/jgretz/node-bits-mongo)
The mongo bit allows you to connect to a mongo database and expose this connection to other bits.

For example, combining this bit with the "code bit" and the "rest bit" will allow you to define your schema in files, and have a fully functional rest setup up with a mongo backend simply by connecting the a couple bits.

Visit the [repo](https://github.com/jgretz/node-bits-mongo) to find out more specifics.

### [NodeBits-Sql](https://github.com/jgretz/node-bits-sql)
The sql bit allows you to connect to a sql database and expose this connection to other bits.

For example, combining this bit with the "code bit" and the "rest bit" will allow you to define your schema in files, and have a fully functional rest setup up with a sql backend simply by connecting the a couple bits.

Visit the [repo](https://github.com/jgretz/node-bits-sql) to find out more specifics.

### [NodeBits-SPA](https://github.com/jgretz/node-bits-spa)
The spa bit allows you to quickly configure hosting a single page app at a specified url

### NodeBits-Admin

### NodeBits-Dynamic-Schema
