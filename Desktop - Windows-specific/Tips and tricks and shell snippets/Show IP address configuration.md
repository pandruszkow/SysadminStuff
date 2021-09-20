Show IP address configuration
=============================
This can be done from PowerShell, since apparently some Windows 10 computers don't have `ipconfig` installed for some reason.

Cmd:

	ipconfig /all
	
PowerShell:

	Get-NetIPAddress | Format-Table
	
Skip the `| Format-Table` if you want a detailed information dump rather than a nice table.
