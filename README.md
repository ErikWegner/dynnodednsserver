This is an implementation of a dynamic dns server in node.js. Its records can be updated through the DynDNS update protocol.

This application has these features:

* IPv4 DNS server to resolve a hostname to its IPv4 address (A-Record)
* Update the records
 + via DynDNS protocol
 + by checking an individual username and passwort for each host record
 + over http and https (when activated)
* Save the records to a file to have the data available on restart

To run the application, you need the file dyndnsdata. It contains all dns records:

```
[
{"host":"samplehost","user":"username","pass":"passw0rd","ip":"8.9.2.1"},
{"host":"secondhost","user":"alice","pass":"p4ssw0rd","ip":"123.4.5.6"}
]
```

The file dnd.js provides these options:

## port

The udp port for the dns server (default value: 53).

## updateportinsecure

The tcp port for the http update service (default value: 1090)

## updateportsecure

The tcp port for the https update service (default value: 1091)

## usehttps

A boolean value to control, whether the https update service should run.

## Certificate

```
var options = {
 key: fs.readFileSync('server.key'),
 cert: fs.readFileSync('server.crt')
};
```

These two values tell the https service, which files it has to use for the server certificate and the certificate key.

## datafile

This is the name of the permanent data file. It saves the hostnames, usernames, passwords and latest IP addresses.
