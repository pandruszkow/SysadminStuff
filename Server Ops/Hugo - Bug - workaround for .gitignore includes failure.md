## Steps to reproduce

1. On Ubuntu 20.04 LTS, install hugo with `snap install hugo --channel=extended`
1. Replace `~/.gitconfig` with:
  ```ini
  [include]
  	path = .gitconfig.local
  ```
2. Add the following to `~/.gitconfig.local`:
  ```ini
  [user]
  	name = John Smith
  	email = user@example.com
  ```
3. `chmod a+r ~/.gitconfig.local ~/.gitconfig`
3. Run `hugo server`
4. The following error message appears:
  ```
  hugo v0.104.1-8958b8741f552c8024af5194330fbf031544a826+extended linux/amd64 BuildDate=2022-09-26T17:05:45Z VendorInfo=snap:0.104.1
  ERROR 2022/09/29 12:36:01 Failed to read Git log: warning: unable to access '/home/[REDACTED]/.gitconfig.local': Permission denied
  fatal: bad config line 5 in file /home/[REDACTED]/.gitconfig
  WARN 2022/09/29 12:36:01 Expand shortcode is deprecated. Use 'details' instead.
  Error: Error building site: logged 1 error(s)
  Built in 732 ms
  ```
  
  ## Workaround
  
  Follow reproduce steps, but replace `hugo server` with `HUGO_ENABLEGITINFO=false hugo server`.
  
  Failure does not occur.
  
