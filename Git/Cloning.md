# Customise cloning destination

By running the clone command as `git clone <repo URL> <destination directory>`, you can control where your cloned repo ends up. The path can be relative or absolute, and the destination directory will be created if not present.

You can also use `.` as the destination directory, which will clone the repo contents directly into your working directory (this has come in handy a few times).

# Cloning from GitHub

Use the SSH URL provided to clone it read-write. Then it doesn't ask for HTTPS username/password, and uses SSH public key authentication instead.
