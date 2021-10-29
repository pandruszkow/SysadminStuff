# Removing data from history after the fact

To retroactively erase all history of a particular directory ever existing in your repo's history, run the command below:

`git filter-branch --tree-filter 'rm -rf <directory>' --prune-empty HEAD`

The same method works for files too.

# Rebasing

Rebasing the first commit
---

To rebase the first commit of your repo (to edit the commit message, etc.), run `git rebase -i --root`.

(With thanks to torek at https://stackoverflow.com/a/23000315)


#Staging

## Selective staging of changes
If you have made changes in more than one part of a file, Git will also allow you to select which ones go into the staging area. Simply run the command as follows:

`git add -p <file>` 

Git will now go through each fragment of the file that's been changed and show you a diff between the old and new version. You can choose to accept/reject/edit etc each fragment as you see fit.

**TODO:** figure out how to make this a BBS-style option selection, so that Git moves directly to the next fragment as soon as `y`/`n` is pressed on the keyboard.


# Cloning

## Customise cloning destination

By running the clone command as `git clone <repo URL> <destination directory>`, you can control where your cloned repo ends up. The path can be relative or absolute, and the destination directory will be created if not present.

You can also use `.` as the destination directory, which will clone the repo contents directly into your working directory (this has come in handy a few times).

## Cloning from GitHub

Use the SSH URL provided to clone it read-write. Then it doesn't ask for HTTPS username/password, and uses SSH public key authentication instead.
