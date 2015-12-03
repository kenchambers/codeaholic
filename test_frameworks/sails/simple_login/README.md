# simple_login

a [Sails](http://sailsjs.org) application


### NOTES:

#### Sales setup is easy

point your terminal to a directory you want to install sails into

*PREREQUISITES*:
  1. NODE
  2. MongoDB (or some db)
  3. Brew

navigate to your directory in the terminal and type:

`
brew install node
npm install sails -g

sails new testProject
`

This will populate your folder with a sails boiler plate which will include an entire folder tree of controllers/models and such

### Simple login

##### Users controller:

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

  'get /login': {
    view: 'login'
  },

  'post /login':
      'UserController.login'



};

```
