Description:
Calculating the energy of each pixel:
I have filled the borders of energy array with 1000
(A pixel is on the border when its row or column is the first or last one)
The energy of the remaining pixels is calculated by squaring the top, bottom, 
left and right pixels and then taking the sqaure root of it.

There is a helper function named find_min_of_above3 which takes in an array and the row and column numbers
as parameters. If the given column is the first column of the array then I only consider the energy
values exactly on top and the top right because the left one doesn't exist.
If the column number is the last column of the array then I only consider the top and top-left column 
since the top-right one doesn't exist.
This function returns the index of the column above that contains the minimum value.

To find the vertical seam:
I have used dynamic programming to find the seam with least energy values.
I have created a 2-D array named dynamic table which stores the sum of minimum energy valued seam till now.
The top row of that table is filled with 1000 since no other pixels exist before that row. 
For the remaining rows, I use the find_min_of_above3 function to find the minimum seam sum and add to to the current
energy value. This recomputing table is used till the last row which then contains the total
minimum seam energy sum. 

Then using a for loop, I get the least sum from the last row and the index of the column that contains this sum.
The seam array contains column numbers from the top row to the last and since I'm backtracing from the last row,
I am filling seam from the end. I use the find_min_of_above3 function to find the minimum column till the top.

Correctness:
