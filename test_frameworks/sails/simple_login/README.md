# simple_login

a [Sails](http://sailsjs.org) application


### NOTES:

#### Sails setup is easy!

point your terminal to a directory you want to install sails into

*PREREQUISITES*:
  1. NODE
  2. MongoDB (or some db)
  3. Brew

navigate to your directory in the terminal and type:

```terminal
brew install node
npm install sails -g

sails new testProject
```

This will populate your folder with a sails boiler plate which will include an entire folder tree of controllers/models and such

### Simple login

#### Users controller:

type this in the terminal:

```javascript
$ sails generate controller <controller name> [action names separated by spaces...]
```

this command will generate a users controller `api/controllers/Users.js`

```javascript
/**
 * CommentController.js
 *
 * @description :: Server-side logic for managing comments.
 */

module.exports = {

  /**
   * CommentController.create()
   */
  create: function (req, res) {
    return res.json({
      todo: 'Not implemented yet!'
    });
  },

  /**
   * CommentController.destroy()
   */
  destroy: function (req, res) {
    return res.json({
      todo: 'Not implemented yet!'
    });
  },

  /**
   * CommentController.tag()
   */
  tag: function (req, res) {
    return res.json({
      todo: 'Not implemented yet!'
    });
  },

  /**
   * CommentController.like()
   */
  like: function (req, res) {
    return res.json({
      todo: 'Not implemented yet!'
    });
  }
};
```

##### Routes.js

- in `config/routes.js` you can use HTTP verbs and paths to point to a controller or a view:
- for this example i have a get to `/login` to display the view and a post to `/login` for when the user presses submit
- simply create a view inside of `/views` and name it

```javascript
module.exports.routes = {

  '/': {
    view: 'homepage'
  },
  // renders view, points towards *.ejs inside of /views
  'get /login': {
    view: 'login'
  },
  //posts directly to login function in users controller
  'post /login':
      'UserController.login'
};

```

#### Users model:

type this in the terminal:

```
$ sails generate model <model name> [attribute1:type1, attribute2:type2 ... ]

```

for example lets generate a model for user with **name/email/password:** :

type this in the terminal:
```
$ sails generate model User name:string email:string password:string
```

this command will generate the following pre formatted model:

```javascript
/**
* User.js
*
* @description :: TODO: You might write a short summary of how this model works and what it represents here.
* @docs        :: http://sailsjs.org/#!documentation/models
*/

module.exports = {

  attributes: {

    name : { type: 'string' },

    email : { type: 'string' },

    password : { type: 'string' }
  }
};

```

#### Tests

sails uses ![mocha](http://mochajs.org/) to run its Server-side tests.

Our first step  a folder structure inside the `/api` folder

```javascript
./myApp
├── api
├── assets
├── ...
├── test
│  ├── unit
│  │  ├── controllers
│  │  │  └── UsersController.test.js
│  │  ├── models
│  │  │  └── Users.test.js
│  │  └── ...
│  ├── fixtures
│  ├── ...
│  ├── bootstrap.test.js
│  └── mocha.opts
└── views

```
#### bootstrap.test.js

Now that we have our folder schema for tests we need to plug in sails via `bootstrap.test.js`

**this is where you can load your fixtures for tests (see below)**

_This file is useful when you want to execute some code before and after running your tests(e.g. lifting and lowering your sails application). Since your models are converted to waterline collections on lift, it is necessary to lift your sailsApp before trying to test them (This applies similarly to controllers and other parts of your app, so be sure to call this file first)._


```javascript

var Sails = require('sails'),
  sails;

before(function(done) {

  // Increase the Mocha timeout so that Sails has enough time to lift.
  this.timeout(5000);

  Sails.lift({
    // configuration for testing purposes
  }, function(err, server) {
    sails = server;
    if (err) return done(err);
    // here you can load fixtures, etc.
    done(err, sails);
  });
});

after(function(done) {
  // here you can clear fixtures, etc.
  Sails.lower(done);
});

```
