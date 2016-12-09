To ensure security of data, many data service providers either enable or require that network traffic is limited to known, predictable locations - trusted clients or peers - identified by static IP addresses.

IBM Bluemix applications run within an environment which dynamically re-assigns IP addresses to outbound connections, and in some case, may span a number of data centres and associated network ranges; there is no reliable way to predict the IP address a Bluemix application may use to connect to a third party data service.

To get around this, [**Statica**](http://support.statica.io/support/solutions/articles/5000614144-ibm-bluemix) has made its proxy service available to Bluemix applications; this allows applications to route/tunnel outbound network traffic via a pair of fixed (static) IP addresses. These IP addresses can then be reliably added to data service firewall *whitelists* or *ACLs* (access control lists).

In this module, you will have the opportunity to try three options for making use of this approach:

1. application-initiated http/https request via proxy
1. service access client library (e.g. **MYSQL**) stream via proxy
1. service access client library (e.g. **MongoDB**) forwarded connection
