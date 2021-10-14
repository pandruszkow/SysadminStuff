## Use a jump host/proxy/bastion to access a different host

SSH supports this natively. To activate this feature, run the SSH command like this:

```shell
ssh -o "ProxyJump=bastionhost.example.com" user@internalhost.example.com
```

Or add it to your `.ssh/config` file like so:

```
Host internalhost
  User user
  Hostname internalhost.example.com
  ProxyJump bastionhost.example.com
```

## Forward your SSH agent across different machines

**Note:** SSH agent forwarding **will not** work if you get the "host key identification changed" message that indicates a MITM. There is no way to override this that I found as of yet.

Add something similar to your `.ssh/config`:

```
host hostname.example.com
  ForwardAgent yes
```
