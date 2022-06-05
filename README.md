# N-Queens

![image](https://user-images.githubusercontent.com/100164051/172036886-d53fb0c5-78d8-41f1-ac53-af0ecd299a09.png)

<!-- This content will not appear in the rendered Markdown -->

We should pre-examine how the queens will be placed as a start. For each row can only have one queen, the working solution will be to set 
a queen and then recurse to the next row. Next, we will have to iterate through the possible options, check the cell for validity, 
then set the queen on the board on each row.

To save on space complexity, we only keep track of the different axes of attack in which a queen might be placed. That being said, we will need to 
check the three remaining axes for validity, except the horizontal row.

There exist N possible columns and 2 * N - 1 possible left-downward diagonals and right-downward diagonals. With a constraint of 1 <= N <= 9, 
each of the two diagonal states represents up to 17 bits' worth of data and the vertical state up to 9 bits. We use bit manipulation to efficiently store 
these states.

We should pass he board state in the form of integers (vert, ldiag, rdiag) as parameters for each recursive call to place a queen. 
We can then use bitmasks to check for cell validity before attempting to recurse to the next row.

Once the end of the board is being reached without failing, the result counter (result) is incremented.


**Time Complexity:** O(N!) which represents the maximum number of queens placed

**Space Complexity:** O(N) for the recursion stack
