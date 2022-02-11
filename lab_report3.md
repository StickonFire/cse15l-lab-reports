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


If successful, you will be prompted for the password. After entering it, you should see some text in this format:

![ImageOfUploadingFiles](https://user-images.githubusercontent.com/70039286/153671009-f37c2edc-8049-4efb-8f91-509877e71724.PNG)

This demonstrates that it works, especially if you see the files you wanted copied within the list.

### Running MarkdownParse on the Remote Server

Now, you can run the files in that directory in the remote server
![Logging into Server](https://user-images.githubusercontent.com/70039286/153673766-d6c251fb-5b87-45eb-aae5-26b472f630ce.PNG)

I made a mistake by trying to compile it here with this command. While one can compile it here with a different command, it would be more efficient to just go to the specific directory, which can be done with this command:

    cd \[directory\]

Here's an example:
![CommandcdExample](https://user-images.githubusercontent.com/70039286/153674403-401f7e62-eea2-4d3b-8d2f-ac6044172cbb.PNG)

You'll know if cd worked if you can see the directory name placed within the command prompt after.

Here's the code getting compiled and running:
![javac MarkdownParse](https://user-images.githubusercontent.com/70039286/153675853-aa3f858a-5eaa-4534-bf8e-e04c208d8161.PNG)
![javac MarkdownParseTest](https://user-images.githubusercontent.com/70039286/153675875-82fe0a6d-0e41-4fb8-891c-7c2fb195712c.PNG)
![Running MarkdownParseTest](https://user-images.githubusercontent.com/70039286/153675908-c87c74ab-2316-41eb-a71e-16dd9e998062.PNG)


### SCP and Run Tests in One Command

Within a single command line, you can insert several commands by placing ";" between it. You can also have a remote system run commands directly from your computer by placing it in quotes after you ssh a server.

With this knowledge, I made this long command line to copy the code to a remote computer and run its tests there.

      scp -r C:\Users\Owner\Documents\GitHub\markdown-parse cs15lwi22zzz@ieng6.ucsd.edu:~/MarkdownParse6;ssh cs15lwi22zzz@ieng6.ucsd.edu "cd MarkdownParse6;javac MarkdownParse.java;javac -cp lib/junit-4.10.jar:lib/hamcrest-core-1.3.jar:. MarkdownParseTest.java;java -cp lib/junit-4.10.jar:lib/hamcrest-core-1.3.jar:. org.junit.runner.JUnitCore MarkdownParseTest"

Unfortunately, this didn't really work well in practice. Initially, it was running fairly fine, prompting me for a password to copy the files, and then to log in. The files were also clearly copied, as seen here:
![Running Oneliner](https://user-images.githubusercontent.com/70039286/153683781-b847977b-2050-406e-9a38-8460b11eea89.PNG)

However, there were issues starting at the "javac MarkdownParse.java" part of the command. It seems as though the system couldn't recognize java.nio.File:
![FileSeemsNotRecognized](https://user-images.githubusercontent.com/70039286/153684342-d7bf4d5b-226f-435b-be0a-12627afb281a.PNG)

This was a very important command for the rest to run, so the next commands, one to compile MarkdownParseTest.java and another to run the tests, ended up failing. Weirdly, running them individually within the remote server works.
