# SimpleBITSServer (Background Intelligent Transfer Service)

A simple python implementation of a BITS server. BITS protocol is used to transfer files asynchronously between a client and a server.
The BITS protocol metadata communication resides mainly in BITS-defined HTTP headers, all start with prefix "BITS-". For that reason, this implemantation is based on python's built-in SimpleHTTPRequestHandler.

The implementation corresponds to the [MSDN specification](https://msdn.microsoft.com/en-us/library/windows/desktop/aa362828(v=vs.85).aspx) for client and server packets.

* It was originally developed as an ad-hoc utility for modelling a BITS upload job scenario.
* The corresponding client is Windows' built-in PowerShell cmdlet.
* Therefore, It is not intended to fully implement or abide to the official specification.
  Further work may be done in the future to expand the specification coverage.

## Background

[Official protocol specification](https://winprotocoldoc.blob.core.windows.net/productionwindowsarchives/MC-BUP/[MC-BUP].pdf) - Background Intelligent Transfer Service (BITS)

[Example use at SafeBreach Labs](https://safebreach.com/Post/Building-a-Python-BITS-Server)

## Usage

### Server
* Tested with Python 2.7:

```
python SimpleBITSServer.py [port]
```

### Client
Prerequisites:
* Must run on a Windows OS to use the Microsoft Windows BITS Service.
 * Ports or protocol mimics might exist, please inform us if you do find
* a BITS client, preferably PowerShell's Start-BitsTransfer. Alternatively:
 * Windows' built in utility - bitsadmin.exe (deprecated)
 * Any program implementing the required interfaces as described on [MSDN](https://msdn.microsoft.com/en-us/library/windows/desktop/aa362820(v=vs.85).aspx)


The simple PowerShell usage this server was built to service:

```
> Import-Module BitsTransfer
> Start-BitsTransfer -TransferType Upload -Source C:\temp\to_upload.txt -Destination http://127.0.0.1/to_upload.txt -DisplayName TEST
```

## Authors

**Dor Azouri** - *Initial work*

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

[WTFPL](http://www.wtfpl.net/) - do What the Fuck You Want To Public License
