---
lodash: true
---

## NodeJS API Tutorial

<div class="package" style="text-align: center;">
  <blockquote>
    <a href="@@base_url@@/node-auth0/master/create-package?path=examples/nodejs-api&type=server@@account.clientParam@@" class="btn btn-lg btn-success btn-package" style="text-transform: uppercase; color: white">
      <span style="display: block">Download a Seed project</span>
      <% if (account.userName) { %> 
      <span class="smaller" style="display:block; font-size: 11px">with your Auth0 API Keys already set and configured</span>
      <% } %>
    </a> 
  </blockquote>
</div>

**Otherwise, Please follow the steps below to configure your existing NodeJS app to use it with Auth0.**

### 1. Add express-jwt dependency

You need to add the express-jwt dependency.

Just run the following code to install the dependency and add it to your `package.json`

````js
npm install express-jwt --save
```

### 2. Configure express-jwt with your Auth0 account

You need to set the ClientID and ClientSecret in `express-jwt`'s configuration so that it can validate and sign [JWT](@@base_url@@/jwt)s for you.

````js
  var express = require('express');
  var app = express();
  var jwt = require('express-jwt');

  var jwtCheck = jwt({
    secret: new Buffer('<%= account.clientSecret %>', 'base64'),
    audience: '<%= account.clientId %>'
  });
```

### 3. Secure your API

Now, you need to specify one or more routes or paths that you want to protect, so that only users with the correct JWT will be able to do the request.

````js
app.use('/api/path-you-want-to-protect', jwtCheck);
```

### 4. You've nailed it.

Now you have both your FrontEnd and Backend configured to use Auth0. Congrats, you're awesome!
