Last updated: 2023-03-04 12:41

### Xargs

Read items from stdin, delimited by blanks (default) and executes provided command with any arguments. If multiple lines are provided -- these are ignored.  
Typically we'll want to pipe **stdout** from one command into `xargs` to do some manipulation.  

_example_:  
```shell
$ ls -lt
total 12
drwxr-xr-x 4 zt zt 4096 Mar  3 11:22 yggdrasil
-rw-r--r-- 1 zt zt 3443 Feb 27 15:38 answers_updated.md
drwxr-xr-x 6 zt zt 4096 Feb 26 22:52 leetcode
```

```shell
$ ls | sort | grep -v ".md" | xargs du -sh
30M	    leetcode
204K	yggdrasil
```
