# Lab Report 2

## Edge Case 1

## Edge Case 2
Link to [file](https://github.com/StickonFire/markdown-parse/blob/main/edge_case2.md) containing edge case2.
Here's the [link](https://github.com/StickonFire/markdown-parse/commit/7a5e2a3e07556c1284ca405cf7336464b093212a) to the changes made due to Edge Case 2.

Edge case 2 consists of an empty "\[\]\(\)", resulting in an empty string getting added into the resulting list of links, along with an actual link to google after that to show that there is an empty string in the list. The code did not care about what was inside of the parentheses, just that it was enclosed in parentheses preceded by an enclosed pair of brackets.
This is an issue because most individuals would not expect an empty string to be considered a link. 
![PictureOfEdgeCase2Result](https://user-images.githubusercontent.com/70039286/151626560-9e94b70e-ca46-460f-aaf5-1c878d39c19d.PNG)

To remedy this, a lower bound of length 3 was placed on all strings placed within the list. This blocked empty strings, resulting the new output to appear like this:
![EdgeCase2PreferredResult](https://user-images.githubusercontent.com/70039286/151626820-7b6f0706-21c5-4b32-93f3-1be11678bf69.PNG)

## Edge Case 3

