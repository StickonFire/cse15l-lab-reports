# Lab Report 3
## Copying a Whole Directory

### Just Copying a Directory
Generally, the command to copy a directory looks like this:
  
scp -r \[directory name\] \[server name\]:~/\[folder name\]

Of course \[directory name\] is the name of the directory to copy, \[server name\] the name of the server the contents are copied to, and \[folder name\]
 the name of the folder within the server to place the contents in. Don't worry if the folder you want to copy the contents to doesn't exist in the remote server; the server should be able to create one.
