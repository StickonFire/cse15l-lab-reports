# Lab Report 5
## Two Implementations, Two Errors

## Set Up

Unlike the Wk9 MarkdownParse, my MarkdownParse implementation wasn't really touched for quite a while, so it is very outdated.

One of the major files to add is a bash script, which I copied over from the Wk9 MarkdownParse. It looks like this:

![script sh for Lab Report 5](https://user-images.githubusercontent.com/70039286/157979273-dd21819b-05b4-4e67-b006-2d92bf53d3c3.PNG)

The goal was to get the results printed within a results.txt for each implementation, so that I can call diff on the two results file.
The resulting script came out like this:
![Script sh for running all for diff](https://user-images.githubusercontent.com/70039286/157987156-6475c09e-d329-490b-9012-5e9d7bad3fac.PNG)


### Difference 1: Infinite Loops

On test-files/12.md, an infinite loop appears to have occurred.
![OriginalMkParseInfiniteLoop](https://user-images.githubusercontent.com/70039286/157974046-0d54c913-676c-4513-b62e-76e2531f1f34.PNG)

This issue also appears for the 194.md, 201.md, 531.md, 566.md, 567.md, and more. Luckily, a could ctrl C through all of these loops.

Doing "cat results.txt" results in a spam of 18s, as seen here. It seems to still be outputting these as I can't even scroll down.
![Mass of 18s](https://user-images.githubusercontent.com/70039286/157975008-81b54c99-ee50-4eac-bc1e-c91e64b4c29a.PNG)

Contrast this to Wk9, which lacked any infinite loop, managing to get to the line that prints "done" without any infinite loops.

![Wk9 NoIssuesProof](https://user-images.githubusercontent.com/70039286/157975790-7c247ab8-6bc2-4702-9d31-abb1dbfde01f.PNG)

Wk9's results displays an empty arrayList as the result for 12.md.
![12 md Wk9 result](https://user-images.githubusercontent.com/70039286/157976748-30da31f3-688e-4882-8a9f-27611ae64e51.PNG)

I believe that Wk9 returned the correct result, as the file had no links within it.
![12 md contents](https://user-images.githubusercontent.com/70039286/157977020-c5b3ef77-c8fd-41e1-85dc-af7e65b46d01.PNG)

## Difference 1 Bug

Looking at each of the files that caused an infinite loop, there was one similarity: a set of brackets without parentheses. Clearly, the issue is that the program failed to find parentheses, and returned -1, resulting in an issue in a while loop. 
![Image of 194](https://user-images.githubusercontent.com/70039286/157983817-5eff74a4-6040-4c7d-aead-4ba7db193686.PNG)
Image of 194.md, one of the files that caused an infinite loop.

Looking into my implementation, it appears that I forgot to fix the infinite loop that occurs if it can't find any parentheses. 

![OriginalOriginalifStatement](https://user-images.githubusercontent.com/70039286/157990810-7867636f-95bb-4185-ab8d-d6dce81490f5.PNG)

So I modified it to deal with this issue:
![New if statement to deal with all outputting -1](https://user-images.githubusercontent.com/70039286/157985643-40172715-9bed-4307-82c5-afc375a26606.PNG)

Now, instead of just dealing with nextOpenBracket being -1, it can deal with all the other variables.


## Difference 2 

Now the script(the one in the second picture under Set Up) can run properly. After running it, I saw how many differences there were in results. One I found interesting was this:
![Difference](https://user-images.githubusercontent.com/70039286/157993486-7f86fffa-395a-406e-9173-ed6058104c7b.PNG)

This seems to say that at line 966 to 968 of results.txt from my implementation differed from line 912 of the Week 9 impelmentation.
While my implementation picked up what it thinks to be a link, the Week 9 implementation got nothing.

This appears to be the results from test file 509.md.

### Difference 2 Bug

Based on the VSCode preview, there should be a link found in the file.
![509 md Test](https://user-images.githubusercontent.com/70039286/157994412-f47c2502-f37a-474a-aaf3-ee3e858c668d.PNG)

This means that the more correct result came from my implementation. This is certainly interesting to me, as I fully expected my implementation to always be more incorrect. My implementation is still incorrect, just less so.

The bug in the Week 9 implementation appears to be here:
![Wk9 Fail spot](https://user-images.githubusercontent.com/70039286/157995072-584550d9-a655-46bc-9bd5-22b2a5c34227.PNG)

The implementation immediately discards any potential links that has a new line or a space within it. This appears to be incorrect.

My implementation, however, is still wrong. Opening the preview of 509.md in github let me copy the link from there. It appears that the correct answer might actually be "uri". Copying and pasting the link resulted in this:
![Resulting Link](https://user-images.githubusercontent.com/70039286/157995427-53273265-bdae-43b4-943c-0e20125cbe56.PNG)

While I'm not sure where the most of the link came from, I know that the only part of the md file that appeared in the link is "uri". I assume that the part in quotation marks was only to provide a title when the link is hovered over, as seen here:
![Infohover](https://user-images.githubusercontent.com/70039286/157995657-e946a29d-5901-4b1a-9bb4-f74820d4a601.PNG)


For my implementation, I think that the bug is that there is no check for these quotation marks to remove the section from the potential link. The check should likely be placed just before toReturn.add call. It should check the link for one quote mark, then find the other, then remove the part between the quotation marks.
![Link Processing Section](https://user-images.githubusercontent.com/70039286/157995831-6ab3238d-830f-4607-abdf-4a890672519d.PNG)
