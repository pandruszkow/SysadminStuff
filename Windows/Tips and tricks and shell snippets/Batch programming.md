Script path and working directories
---

The following variables are available:
 
Variable name | Meaning
--------------|--------
`%0`          | full path to the script, including the filename
`%~dp0`       | (d)rive and (p)ath to the script, but with the filename omitted.<br>Equivalent to ```dirname `pwd`/filename.txt``` on Linux.
`%cd%`        | the current working directory

(Source: https://ss64.com/nt/syntax-args.html/ . This site looks like a good resource in general.)
