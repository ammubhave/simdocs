---
title: Simmons API

language_tabs:
  - javascript

search: true
---

# Introduction

Welcome to the Simmons API! You can use our API to access Simmons API endpoints, which can get information on people, profiles, packages, etc. from our database.

```
<script src="http://code.jquery.com/jquery-1.11.2.min.js"></script>
<script src="https://simmons-dev.mit.edu/api/static/js/simmons-api.js"></script>
```

# OAuth and Client ID

```javascript
sim.init({
    'clientid': 'CLIENT_ID'
});
```

You will need to get an OAuth2 Client ID. Knock on Amol's door and he will give you one.

After including `simmons-api.js` in your application, you need to call `sim.init()` method before you can start using the Simmons javascript API.

> Make sure to replace `CLIENT_ID` with your Client ID.

<aside class="notice">
You must replace `CLIENT_ID` with your Client ID.
</aside>

## Testing on your local machine
You can use the api from `localhost`.
You need to use the client id as `efVV8LnWW5f6XxmJE3xexSjAPgjr0nMCyAyMGMvn`
You still need to knock on Amol's door to get authorization to use the API on a non-localhost host.

You can run a local server on `localhost` by running the command `python -m SimpleHTTPServer 8000` from the directory where you want to server. Remember that there is CORS check for localhost.

# Authentication

## Login

```javascript
sim.login();
```

Once you have called `sim.init()` method, you can require users to login by calling `sim.login()`. This function call redirect your application to the Simmons Authentication page where the user will be asked to login (automatically via certs or by username/password). After successful login, the the Simmons Authentication page will automatically redirect to the current page.

If the user was not able to successfully login, Simmons Authentication will show a 401 Forbidden page.

# People

## Get all people

```javascript
sim.people.all(function (data) {
    console.log('I just got a list of all residents! Here it is:');
    console.log(data);
});
```

To get a list of all residents, use the `sim.people.all(success)` method. If the call was succeeds, the `success` callback will be called with the parameter `data` begin a list of all residents.

## Get the profile of a specific person

Use the `sim.people.get(username, success)` method to get the profile of a specific person. If the request succeeds, the `success` callback will be called with `data` containing the profile data of that user.

```javascript
sim.people.get(username, function (data) {
    console.log('Here is all the information for the username ' + username);
    console.log(data);
});
```

# Example

The following is an example HTML using the API.

```html
<html>
<head>
    <script src="http://code.jquery.com/jquery-1.11.2.min.js"></script>
    <script src="http://simmons-dev.mit.edu/api/static/js/simmons-api.js"></script>

    <script>
        sim.init({
            'clientid': 'efVV8LnWW5f6XxmJE3xexSjAPgjr0nMCyAyMGMvn'
        });
        sim.login();
        sim.people.all(function(data) {
            for (var i = 0; i < data.length && i < 20; i++) {
                console.log(data[i]);
                $('#res').append($('<div>').text(data[i].username));
            }
        })
        sim.people.get('ambhave', function(data) {
            console.log(data);
        })
    </script>
</head>
<body>
    <h1>All Residents (limited to 20):</h1>
    <div id='res'></div>
</body>
</html>
```

Put this code in a .html file and run `python -m SimpleHTTPServer 8000`, then goto `http://localhost:8000/` and then click on your file.