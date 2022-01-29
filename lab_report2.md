# Lab Report 2

## Edge Case 1
Link to [file](https://github.com/StickonFire/markdown-parse/blob/main/edge-case.md) containing edge case 1.

Link to [commit](https://github.com/StickonFire/markdown-parse/commit/70e973d1cd44980826a49f44a9ec3575764a1fda) made to remedy the first issue of Edge Case 1.

The first Edge Case has a few bugs, but the most egregious is some infinite loop. This infinite loop is caused by the extra letters placed after one of the ending parentheses. These extra letters resulted in the while loop's end conditions to not fire before the program searched for another link. When the loop started again, the first line of the loop returned -1, as it couldn't find a start bracket indicating a possible start of a new link. Due to this, the next lines searched entire String again, resulting in the exact same circumstances. Due to this, the loop was unable to end.
![InfiniteLoopFromFirstEdgeCase](https://user-images.githubusercontent.com/70039286/151630928-c62ca0ed-8f3c-4ce4-9061-7ddafd42202c.PNG)


To remedy this issue, a new if statement was placed to break the loop if the first statement of the loop results in a -1:
![EdgeCase1InfiniteLoopRemedy](https://user-images.githubusercontent.com/70039286/151629859-dc15c1c4-ad90-4678-98d6-ecb2add4fba9.PNG)
This allowed this infinite loop to end, resulting in this less incorrect output:
![PictureOfEdgeCase1Result](https://user-images.githubusercontent.com/70039286/151630441-3d6c4751-b404-495a-b465-a43059eed25f.PNG)

## Edge Case 2
Link to [file](https://github.com/StickonFire/markdown-parse/blob/main/edge_case2.md) containing edge case2.

[Link](https://github.com/StickonFire/markdown-parse/commit/7a5e2a3e07556c1284ca405cf7336464b093212a) to the changes made due to Edge Case 2.

Edge case 2 consists of an empty "\[\]\(\)" and an actual link to google after that to show that there is an empty string in the list. The code did not care about what was inside of the parentheses, just that it was enclosed in parentheses preceded by an enclosed pair of brackets. This caused an empty string to be included and printed within the list of links.
This is an issue because most individuals would not expect an empty string to be considered a link. 
![PictureOfEdgeCase2Result](https://user-images.githubusercontent.com/70039286/151626560-9e94b70e-ca46-460f-aaf5-1c878d39c19d.PNG)

To remedy this, a lower bound of length 3 was placed on all strings placed within the list.
![EdgeCase2ChangeMade](https://user-images.githubusercontent.com/70039286/151627714-0e11ffee-e5c4-4799-84bb-58fc2452f851.PNG)

This blocked empty strings, resulting the new output to appear like this:
![EdgeCase2PreferredResult](https://user-images.githubusercontent.com/70039286/151626820-7b6f0706-21c5-4b32-93f3-1be11678bf69.PNG)

## Edge Case 3
[Link](https://github.com/StickonFire/markdown-parse/blob/main/edge_case3.md) to file with edge case 3.
[Link](https://github.com/StickonFire/markdown-parse/commit/2f56767365c2e71832ed519b6f9bf5dc04d84a4f) to the commit made due to edge case 3.

Edge case 3 lacks any links and instead has some brackets and parentheses placed in it. Despite this, something was placed in the list, and it's definitely not a link.
![EdgeCase3IncorrectResult](https://user-images.githubusercontent.com/70039286/151636388-2e4afc82-d475-4845-a5c3-2f4ca79fe89e.PNG)

This is due to the system only adding things based on whether it's within parentheses and preceded by brackets. As such, as long as those conditions are true, it will be added, even if it looks nothing like a link. In order to remedy this specific symptom, I added a new condition into the whether a string is added into the list, which is that it requires a period, which I think all links have.
![Edgecase3change](https://user-images.githubusercontent.com/70039286/151637048-5ec38780-f5c1-4dd1-a19f-57d9e09ec340.PNG)

That resulted in the right output, an empty list:
![Edgecase3CorrectResult](https://user-images.githubusercontent.com/70039286/151637098-fc55a144-c6af-4cf7-8029-420d54ca6197.PNG)

While it did fix this specific issue, it certainly isn't a thorough fix. As long as anything in parentheses has a period, it would end up getting placed in the list.

