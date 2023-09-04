# pentesting tools
## PKI on the Fly
Building your own PKI and issuing server, client, and email certificates is often useful during security testing, but the openssl command line interface is not streamlined for this purpose. I wrote PKI on the Fly to make it easy to create and manage a PKI for penetration testing.
```
Example use:
  Create a root CA named MyCa:
   /pkifly.py ca MyCa
  Create a server cert and key signed by MyCa
   ./pkifly.py server MyCa --servername pentest.target.su
  Create TLS client cert and key signed by MyCa
   ./pkifly.py client MyCa --clientname bobsmith
  Create an S/MIME email cert and key signed by MyCA
   ./pkifly.py email MyCa --email bobsmith@target.su
```
See the github repo: [PKI on the Fly](https://github.com/thatnickbrown/pkifly)

## HTTP Header Mirror
Request routers, reverse proxies, load balancers, authentication services, and various other HTTP doodads that sit between clients and backend servers can add or modify headers. HTTP Header Mirror is a web server that prints every header it receives to the page body, simplifying the process of testing for header injection vulnerabilities. HTTP Header Mirror has been helpful in discovering numerous vulnerabilities, including an issue with a CVSS 3.1 Base Score of 10 in a widely used product.

See the github repo: [HTTP Header Mirror](https://github.com/thatnickbrown/hhmirror)
