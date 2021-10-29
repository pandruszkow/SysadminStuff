# Removing data from history after the fact

To retroactively erase all history of a particular directory ever existing in your repo's history, run the command below:

`git filter-branch --tree-filter 'rm -rf <directory>' --prune-empty HEAD`

The same method works for files too. There are other, safer methods for doing this, but they may not be available if installation of additional software is not permitted, or if there is a requirement to use an older version of Git. For example, the `git filter-repo` command will not work on the latest version of Git available from the official software repos for Ubuntu 18.04 LTS.

(src: https://stackoverflow.com/a/33493108)

# Rebasing

Rebasing the first commit
---

To rebase the first commit of your repo (to edit the commit message, etc.), run `git rebase -i --root`.

(With thanks to torek at https://stackoverflow.com/a/23000315)


# Staging

## Selective staging of changes
If you have made changes in more than one part of a file, Git will also allow you to select which ones go into the staging area. Simply run the command as follows:

`git add -p <file>` 

Git will now go through each fragment of the file that's been changed and show you a diff between the old and new version. You can choose to accept/reject/edit etc each fragment as you see fit.

**TODO:** figure out how to make this a BBS-style option selection, so that Git moves directly to the next fragment as soon as `y`/`n` is pressed on the keyboard.


# Cloning

## Shallow clone

Sometimes, you are only checking out a repo so you can deploy a piece of software, or build something, but won't ever do dev work on it. In that case, cloning the entire repo history is pointless. Change your `git clone` command as follows:

`git clone <repo_url> [<target_directory>]` -> `git clone <repo_url> [<target_directory>] --depth=1`

This will ensure you're only transferring as much data as is required to reconstitute the repo contents at the latest commit, without any history. As a bonus, if the repo used to contain large files that were subsequently erased, you won't have to sit around waiting for them to transfer.

## Customise cloning destination

By running the clone command as `git clone <repo URL> <destination directory>`, you can control where your cloned repo ends up. The path can be relative or absolute, and the destination directory will be created if not present.

You can also use `.` as the destination directory, which will clone the repo contents directly into your working directory (this has come in handy a few times).

## Cloning from GitHub

Use the SSH URL provided to clone it read-write. Then it doesn't ask for HTTPS username/password, and uses SSH public key authentication instead.
