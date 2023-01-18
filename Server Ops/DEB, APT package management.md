### Full package upgrade to the latest version

IIRC, plain `apt upgrade` will skip certain packages like the kernel.

To upgrade the machine fully, run the following instead:

```sh
sudo apt update
sudo apt full-upgrade
```

### Viewing all package versions available from a repository

Run `apt-cache policy <package name>`:

```sh
$ apt-cache policy apache2
apache2:
  Installed: 2.4.53-3+ubuntu20.04.1+deb.sury.org+1
  Candidate: 2.4.54-1+ubuntu20.04.1+deb.sury.org+1
  Version table:
     2.4.54-1+ubuntu20.04.1+deb.sury.org+1 500
        500 http://ppa.launchpad.net/ondrej/apache2/ubuntu focal/main amd64 Packages
 *** 2.4.53-3+ubuntu20.04.1+deb.sury.org+1 100
        100 /var/lib/dpkg/status
     2.4.41-4ubuntu3.12 500
        500 http://de.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
     2.4.41-4ubuntu3 500
        500 http://gb.archive.ubuntu.com/ubuntu focal/main amd64 Packages
```
