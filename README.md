# uipath-orchestrator

This is a Node.JS client for UiPath Orchestrator.

### Table of content

1. [Installation](#installation)
2. [Usage](#usage)
3. [TODO](#todo)
4. [License](#license)

### Installation

*Work in progress - pending npm deployment*

### Usage

Orchestrator is a class and its constructor takes an `option` object.
```javascript
var util = require('util');
var Orchestrator = require('uipath-orchestrator');
var orchestrator = new Orchestrator({
     tenancyName: 'test',           // The Orchestrator Tenancy
     usernameOrEmailAddress: 'xxx',// The Orchestrator login
     password: 'yyy',               // The Orchestrator password
     hostname: 'host.company.com', // The instance hostname
     isSecure: true,                // optional (defaults to true)
     port: 443 // optional (defaults to 80 or 443 based on isSecure)
});
var apiPath = '/odata/Users';
var apiQuery = {};
orchestrator.get(apiPath, apiQuery, function (err, data) {
    if (err) {
        console.error('Error: ' + err);
    }
    console.log('Data: ' + util.inspect(data));
});
```
The 3 supported basic methods are as follows:
```javascript
Orchestrator.get(path, query, callback);
Orchestrator.post(path, data, callback);
Orchestrator.put(path, data, callback);
```
where `query` is an querystring-ready *object*, and `data` a `JSON.stringify`able *object*.

These are very generic methods, and the plan is to expose dedicated helpers in the following form:
```javascript
orchestrator.v2.api.postLogs(postLogsData, callback);
orchestrator.v2.odata.getUsers(getUsersQuery, callback);
``` 

Note that you can play around with these by creating a sandbox tenancy here:
https://demo.uipath.com/

### TODO

This is just the beginning and there is a lot left to do.
If you have suggestions and ideas, please do not hesitate to let me know.
- [ ] Proper unit testing
- [ ] Extend each API version
- [ ] Write wiki
- [ ] Write TS definitions
- [ ] Add DELETE method

### License

MIT
