Auf Basis von Node.js bietet die Software einen DNS-Server an, der über das DynDNS-Protokoll aktualisiert wird.

Dieses Programm bietet die folgenden Funktionen:

* IPv4-DNS-Server zur Auflösung eines Hostnamens in eine IPv4-Adresse (A-Record)
* Aktualisierung der Datensätze
 + über das DynDNS-Protokoll
 + Prüfung einer hostnamenabhängigen Benutzer-Passwort-Kombination
 + über HTTP und HTTPS (wenn aktiviert)
* Ablage der Datensätze in einer Datei, um beim Neustart alle Datensätze bereit zu haben

Für den Betrieb wird die Datei dyndnsdata benötigt. Darin werden die möglichen DNS-Einträge konfiguriert:

```
[
{"host":"samplehost","user":"username","pass":"passw0rd","ip":"8.9.2.1"},
{"host":"secondhost","user":"alice","pass":"p4ssw0rd","ip":"123.4.5.6"}
]
```

In der Datei dnd.js gibt es folgende Parameter:

## port

Angabe des UDP-Ports für den DNS-Server (Standard 53).

## updateportinsecure

Angabe des TCP-Ports für den HTTP-Update-Dienst.

## updateportsecure

Angabe des TCP-Ports für den HTTPS-Update-Dienst.

## usehttps

true/false zur Steuerung, ob der HTTPS-Server gestartet werden soll.

## Zertifikat

```
var options = {
 key: fs.readFileSync('server.key'),
 cert: fs.readFileSync('server.crt')
};
```

Benennt die Zertifikats- und Schlüsseldatei für den HTTPS-Server.

## datafile

Gibt den Dateinamen für die Datei an, in der die möglichen DNS-Einträge, Benutzernamen, Passwörter und gegenwärtigen IP-Adressen stehen.