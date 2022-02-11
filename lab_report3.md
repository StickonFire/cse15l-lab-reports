# Lab Report 3
## Copying a Whole Directory

### Just Copying a Directory
Generally, the command to copy a directory looks like this:
  
scp -r \[directory name\] \[server name\]:~/\[folder name\]

Of course \[directory name\] is the name of the directory to copy, \[server name\] the name of the server the contents are copied to, and \[folder name\]
 the name of the folder within the server to place the contents in. Don't worry if the folder you want to copy the contents to doesn't exist in the remote server; the server should be able to create one.

The most trouble I usually get from trying to copy a directory is that the system can't find the directory I want to copy. Whenever this happens, I try to copy the direct path towards the directory. Sometimes, this is my go-to just to be on the safe side. If you have it already opened in VSCode, the path to the directory should be shown on the prompt before your command.

![Command Prompt](https://user-images.githubusercontent.com/70039286/153667346-e333a31e-8d03-4dec-9984-d44bec758098.PNG)
The highlighted sction is the path to the directory.

**Example: MarkdownParse**
As an example, I'll show the command used to copy my MarkdownParse into my class account

Here's the image (ignore the blue box):
![CommandForSCP](https://user-images.githubusercontent.com/70039286/153670502-da793730-9181-4455-8e99-cfbc0ee18aa1.PNG)
