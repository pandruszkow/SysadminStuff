|Article status|
|--------------|
|Incomplete|

# Port scanning with nmap

### Use cases for sysadmin/devops use
- Obtaining the most up-to-date index of all the server machines/VMs attached to an internal network
- Troubleshooting network outages (to see the service is up, and whether a port is blocked via a firewall/the service is down)
- Troubleshooting end-to-end connectivity issues (checking whether a particular service is reachable from the outside

### Options to `nmap`

|Command line flag/flag combo/argument|Example|Meaning of example|
|----------------------------|-------|------------------|
|`xxx.xxx.xxx.yyy/zz`|138.17.14.95/27|Scan all hosts within the range of a 27-bit netmask of 138.17.14.95 (meaning, hosts from `138.17.14.65` to `138.17.14.94`)|
|`-Pn`||Don't bother with checking that the machine is up before scanning, just scan the ports|
|`-p`|`-p 22,23,443,80,3389`|Scan specified servers for open SSH, Telnet, HTTP, HTTPS and RDP ports|
|`-A`||Discover/probe host/service information (OS, version, misc.)|
|`-O`||Discover/probe host OS only|

### Further work
Create a multiple-choice to run scans from. I don't use nmap often enough to memorise these options.
