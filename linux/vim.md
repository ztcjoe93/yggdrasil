
## '\*' and '\+' registers
 
Reference SO: https://superuser.com/questions/624231/in-vim-what-is-the-difference-between-and-registers  

\* and \+ are X11 features -- any OS that uses X11 will be able to access these registers.  
- "+ register corresponds to the "CLIPBOARD" selection in X11
- "* register corresponds to the "PRIMARY" selection in X11

To yank values into the clipboard register, you can execute `"+y` and use the usual paste to retrieve the data.  