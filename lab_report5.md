# Lab Report 5
## Two Implementations, Two Errors

## Set Up

Unlike the Wk9 MarkdownParse, my MarkdownParse implementation wasn't really touched for quite a while, so it is very outdated.

One of the major files to add is a bash script, which I copied over from the Wk9 MarkdownParse. It looks like this:

//Add image here

The goal of this is to create two results.txt files, and call diff on both of the files. It looked fine, until I tried to run it on my implementation.

### Difference 1: Infinite Loops

On test-files/12.md, an infinite loop appears to have occurred.
![OriginalMkParseInfiniteLoop](https://user-images.githubusercontent.com/70039286/157974046-0d54c913-676c-4513-b62e-76e2531f1f34.PNG)

This issue also appears for the 194.md, 201.md, 531.md, 566.md, 567.md, and more. Luckily, a could ctrl C through all of these loops.

Doing "cat results.txt" results in a spam of 18s, as seen here. It seems to still be outputting these as I can't even scroll down.
![Mass of 18s](https://user-images.githubusercontent.com/70039286/157975008-81b54c99-ee50-4eac-bc1e-c91e64b4c29a.PNG)

Contrast this to Wk9, which lacked any infinite loop, managing to get to the line that prints "done" without any infinite loops.

![Wk9 NoIssuesProof](https://user-images.githubusercontent.com/70039286/157975790-7c247ab8-6bc2-4702-9d31-abb1dbfde01f.PNG)
