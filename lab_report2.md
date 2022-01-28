# Lab Report 2

## Edge Case 1

## Edge Case 2
Link to [file](https://github.com/StickonFire/markdown-parse/blob/main/edge_case2.md) containing edge case2.
Here's the [link](https://github.com/StickonFire/markdown-parse/commit/7a5e2a3e07556c1284ca405cf7336464b093212a) to the changes made due to Edge Case 2.

Edge case 2 consists of an empty "\[\]\(\)" resulting in an empty string getting added into the resulting list of links.
This is an issue because most individuals would not expect an empty string to be considered a link. 

To remedy this, a lower bound of length 3 was placed on all strings placed within the list.
## Edge Case 3
