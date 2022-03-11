# Lab Report 5
## Two Implementations, Two Errors

## Set Up

Unlike the Wk9 MarkdownParse, my MarkdownParse implementation wasn't really touched for quite a while, so it is very outdated.

One of the major files to add is a bash script, which I copied over from the Wk9 MarkdownParse. It looks like this:

//Add image here

The goal of this is to create two results.txt files, and call diff on both of the files. It looked fine, until I tried to run it on my implementation.

### Difference 1: Infinite Loop

On test-files/12.md, an infinite loop appears to have occurred.
![OriginalMkParseInfiniteLoop](https://user-images.githubusercontent.com/70039286/157974046-0d54c913-676c-4513-b62e-76e2531f1f34.PNG)

