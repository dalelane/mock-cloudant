This is a node.js module to mock IBM Cloudant for testing based on mock-couch. See https://github.com/chris-l/mock-couch and http://chris-l.github.io/mock-couch/

In addition to mock-couch, this library provides a basic version of Cloudant's _find endpoint as well as the ability to POST single documents (in addition to POST _bulk_docs).

Installation:
```
npm install --save-dev fubar/mock-cloudant
```

# Example

For convenient usage in tests, consider creating a utility class like:

```javascript
'use strict';

var mockCloudant = require('mock-cloudant');
var MockCouch = mockCloudant.MockCouch; // eslint-disable-line no-unused-vars

class CloudantMock {

  /** @member {MockCouch} CloudantMock#cloudantMockServer */

  start () {
    this.cloudantMockServer = mockCloudant.createServer();
    this.cloudantMockServer.listen(1337);
    this.cloudantMockServer.addDB('users');
  }

  stop () {
    this.cloudantMockServer && this.cloudantMockServer.close();
  }
}

module.exports = CloudantMock;
```
