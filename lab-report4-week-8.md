# Lab Report 4

## Links to MarkdownParses

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

