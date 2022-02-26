# Lab Report 4

## Links to MarkdownParses
[My implementation] (https://github.com/StickonFire/markdown-parse)

[Reviewed implementation](https://github.com/StickonFire/WK7MarkdownParse) 


## Checking What Must be Produced

Before you can effectively produce what links to add as a result, you must know what exactly is considered a link by the markdown file.
To understand this, you can choose to preview the files on VSCode, revealing what the code is supposed to look like.

**Snippet 1**

Previewing the first snippet shows this:
![Snippet1Results](https://user-images.githubusercontent.com/70039286/155800346-0b5ec293-6a01-4a51-b16a-5fb4acd664a4.PNG)

This reveals much about how markdown interacts with backticks.
By the looks of it, these backticks seem to make whatever's within it into text.
However, as seen within line 3, it appears that the backtick was incorporated into the new link.

This preview shows that the only parts markdown considers links are "`google.com", "google.com", and "ucsd.edu"

**Snippet 2**

Previewing the second snippet shows this:
![Snippet2Results](https://user-images.githubusercontent.com/70039286/155801973-0321d205-d7af-4bef-8d85-d4974ed5a6a8.PNG)

Snippet2 shows various cases involving the brackets and parentheses. 
This reveals that a correctly formatted link within the brackets of another will be considered one,
but link that link is nested into isn't considered one.
Line 3 shows that the link includes the two pairs of inner parentheses.
Line 5 shows that escaped brackets can be placed within brackets of a link, seemingly with no effects.

Markdown only considers "a.com", "a.com(())", and "example.com" as links.

**Snippet 3**

Previewing the third snippet shows this:
![Snippet3Results](https://user-images.githubusercontent.com/70039286/155802780-dea8de32-a413-46da-9820-e54e1c337799.PNG)

This snippet appears to show cases involving new lines. Line 1 shows that a few line breaks in the brackets breaks the link.
Link 2 shows that a single line break isn't enough to break a link, and that there seems to be line breaks between the paratheses and link.
Link 3 seems to break due to a lack of a closing bracket, and Link 4 breaks due to multiple line breaks at the end.

Markdown seems to consider only "https://ucsd-cse15l-w22.github.io/" a link.

## JUnit Tests

With these results, a few JUnit tests can now be made.

![JUNITTEST](https://user-images.githubusercontent.com/70039286/155807107-f2ff94e2-a478-40e0-9b0c-a44ac4ba0f11.PNG)

### My Implementation

All of the tests, when ran on my implementation, resulted in an empty list getting returned. This meant that all three failed:

![MyImplementationS1Fail](https://user-images.githubusercontent.com/70039286/155814646-68c4bda9-d196-41ad-8530-7347c7cf464f.PNG)
![MyImplementationS2Fail](https://user-images.githubusercontent.com/70039286/155814657-2e1b1f7f-dc2d-43d2-bdf4-8eda2e9366bf.PNG)
![MyImplementationS3Fail](https://user-images.githubusercontent.com/70039286/155814659-7a693d16-49cf-4851-9ea4-256ed40d5455.PNG)



### Reviewed Implementation

Running these test initially caused the same error wihin all of them, which is closeParen resulting in a StringoutOfBoundsException.
![UnintendedError](https://user-images.githubusercontent.com/70039286/155809310-722deb44-927b-4ab9-b8c3-4b89f54c0d7b.PNG)

However, this wasn't exactly what was being tested, so I fixed it. The issue was that the closeParen function didn't stop when it reached the end of the markdown string. So I added a new if statement to end it there, as seen in the first if statement.
![FixForUnintendedOne](https://user-images.githubusercontent.com/70039286/155809326-e31cedb6-a9d4-4635-94f5-31bc86260c0f.PNG)

After this, all three failed, seemingly with similar errors as my implementation:
![Week8Failures](https://user-images.githubusercontent.com/70039286/155813196-7b3b8c3a-7fee-489c-9f8b-3cd77e5540a0.PNG)

All of the tests come back with an empty list.


## What to Change?

### Inline code with backticks

I may be underestimating the difficulty to do this, but it seems as though you can make the code watch for two backticks and ignore whatever's between them. 
If the program finds a single backtick within the parentheses part of the link, it ignores that there's a backtick there and includes it within the link, as seen in the second link attempt of snippet 1.
For singular backticks, perhaps have the program ignore it if there is multiple new lines between it and the next backtick or there are no backticks between it and the end of the file.

### Nest parentheses, brackets, escaped brackets

It looks as though the reviewed implementation effectively should have the answer for nest parentheses, which could be a good base for the brackets too. Escaped brackets should also be easy to deal with, as the program can check the previous character for a "\" and ignore the bracket if this is found. Nested links is a unique case, and will require major changes (over 10 lines). The system has to look for these links within the brackets, which could be helped by perhaps calling getLinks on the space between the brackets. If one is found, it will plant that within the links found, discard the link that link was nested in, and continue on.

### Newlines in brackets and parentheses

If a more than one continuous new line is found between the brackets of a potential link, it should immediately discard the potential link and continue on. At the parentheses, it appears that a single new line on the edge shouldn't matter, but if multiple pop up at either end, the getLinks should discard the potential link and continue.
