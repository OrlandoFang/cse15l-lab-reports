## Lab report 5
## Link to test files
[test files](https://github.com/nidhidhamnani/markdown-parser/tree/main/test-files)

## Find differences
I used vimdiff on the results of running a bash for loop.

## Difference 1
For the test on test file 489.md, my implementation gave the wrong output and the provided implementation gave the correct output.

Actual outputs: Result of my implementation is on left, provided implementation's result is on right
![diff1result](diff1result.png)

Expected output is that there is no valid link
![diff1expected](diff1expected.png)

Finding Bug:

![diff1code](diff1code.png)

The bug is that the method does not check if there exist new lines between brackets and parentheses, so my implementation outputed the link because it assumed that this link is valid as long as there exist a open parentheses and a close parentheses.
To fix this bug, before the line ```int closeParen = markdown.indexOf(")", openParen);``` i should add if statements that checks if there exist a new line ```"\n"``` between the open and close parentheses.

## Difference 2
For the test on test file 494.md, my implementation gave the wrong output and the provided implementation gave the correct output.

Actual outputs: Result of my implementation is on left, provided implementation's result is on right
![diff2result](diff2result.png)

Expected output is that ```(\(foo\))``` is a valid link with the name ```link```
![diff2expected](diff2expected.png)

Finding Bug:

![diff2code](diff2code.png)

The bug is that the output of my implementation missed the close parentheses within the link. This is because my implementation define the close parentheses that was found first as the end of the link.
To fix this bug, before the line ```int closeParen = markdown.indexOf(")", openParen);``` i should add if statements that check if there exist another close parentheses before the next new line or the next link.
