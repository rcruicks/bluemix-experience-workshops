## Static addresses for firewalls and access control lists

To ensure security of data, many data service providers either enable or require that network traffic is limited to known, predictable locations - trusted clients or peers - identified by static IP addresses.

IBM Bluemix applications run within an environment which dynamically re-assigns IP addresses to outbound connections, and in some case, may span a number of data centres and associated network ranges; there is no reliable way to predict the IP address a Bluemix application may use to connect to a third party data service.

To get around this, [**Statica**](http://support.statica.io/support/solutions/articles/5000614144-ibm-bluemix) has made its proxy service available to Bluemix applications; this allows applications to route/tunnel outbound network traffic via a pair of fixed (static) IP addresses. These IP addresses can then be reliably added to data service firewall *whitelists* or *ACLs* (access control lists).

In this module, you will have the opportunity to try three options for making use of this approach:

1. application-initiated http/https request via proxy
1. service access client library (e.g. **MYSQL**) stream via SOCKS
1. service access client library (e.g. **MongoDB**) forwarded connection

### make proxy-enabled requests

By using *request* services which are proxy aware, most language runtimes can provide a mechanism to exploit the Statica service.

Import the appropriate library/module, and configure with the Statica proxy connection URL

+ Ruby
``` ruby
require "rest-client"
RestClient.proxy = ENV["STATICA_URL"] if ENV["STATICA_URL"]
res = RestClient.get("http://ip.jsontest.com")
puts "Your IP was: #{res.body}"
```
+ node
``` javascript
var request = require('request');
var options = {
                proxy: process.env.STATICA_URL,
                url: 'http://ip.jsontest.com/',
                headers: {
                  'User-Agent': 'node.js'
                }
              };

  function callback(error, response, body) {
    if (!error && response.statusCode == 200) {
    console.log(body);
    }
  }

request(options, callback);
```

### proxy enabled client services

Some application service clients have been built with inherent support for proxying  - *mysql* and *ftp* being two common examples.

The client code needs minor configuration to take advantage of the Statica proxy:

+ [mysql via proxy](http://support.statica.io/support/solutions/articles/5000543888-accessing-a-mysql-database-via-a-static-ip-from-node-js-)
+ [FTP server](http://support.statica.io/support/solutions/articles/5000544264-accessing-an-ftp-server-from-a-static-ip-in-php)

Environments where the client cannot be configured to directly exploit SOCKS or proxy connections, Statica offers a *wrapper* module which can be used to route some or all outbound connections from an application via the SOCKS service. This requires installing the wrapper module - [download from 
