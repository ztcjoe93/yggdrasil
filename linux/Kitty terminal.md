Last updated: 2023-03-08 22:51

## 'xterm-kitty': unknown terminal type

When kitty is used to ssh into a remote that does not have its terminfo, various issues can occur. The solution is normally to copy over the terminfo. Kitty has an ssh kitten to automate exactly this.

```shell
$ kitty +kitten ssh user@host
```

References:  
- https://wiki.archlinux.org/title/Kitty#Terminal_issues_with_SSH
- https://sw.kovidgoyal.net/kitty/faq/#i-get-errors-about-the-terminal-being-unknown-or-opening-the-terminal-failing-or-functional-keys-like-arrow-keys-don-t-work
