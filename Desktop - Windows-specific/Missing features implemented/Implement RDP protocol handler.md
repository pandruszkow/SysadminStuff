# Add support for `rdp://` URLs in Windows 7+

By default, Windows doesn't understand `rdp://` URLs. Here's how to manually add support for them using a custom RDP protocol handler:

1. Create a file named `protocol-handler-rdp.js` in `C:/Windows`

2. Paste the following code inside. This will handle parsing of the URL and handing off the server address to the RDP client:
```javascript
var rdpUrl = (WScript.Arguments(0))
var rdpProtoPrefix = 'rdp://'
var rdpClientAppPath ='C:\\Windows\\system32\\mstsc.exe'

//Remove the leading `rdp://` and the trailing slash from the URL for passing to the RDP client application
rdpUrl = rdpUrl.replace(rdpProtoPrefix, '').replace('/', '')
var shell = new ActiveXObject("WScript.Shell")
shell.Exec(rdpClientAppPath + " /v:" + rdpUrl)
```
  
3. Run the following `regedit` commands to register the protocol handler:
```bash
reg add "HKCR\rdp" /f /v "" /t REG_SZ /d "URL:Remote Desktop Connection"
reg add "HKCR\rdp" /f /v "URL Protocol" /t REG_SZ /d ""
reg add "HKCR\rdp\DefaultIcon" /f /v "" /t REG_SZ /d "C:\WINDOWS\System32\mstsc.exe"
reg add "HKCR\rdp\shell\open\command" /f /v "" /t REG_SZ /d "wscript.exe C:\WINDOWS\protocol-handler-rdp.js %1"
```

(Thanks and all credit to James Clements over at http://www.jjclements.co.uk/2010/02/21/rdp-hyperlink/. I've rewritten the JS code a bit to make it more concise and descriptive so that I know what's going on)
