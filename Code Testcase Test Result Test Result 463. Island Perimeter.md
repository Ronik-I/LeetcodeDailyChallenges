# QUESTION : 463. Island Perimeter

You are given row x col grid representing a map where grid[i][j] = 1 represents land and grid[i][j] = 0 represents water.

Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells).

The island doesn't have "lakes", meaning the water inside isn't connected to the water around the island. One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.

## Example 1:  <br>
Input: grid = [[0,1,0,0],[1,1,1,0],[0,1,0,0],[1,1,0,0]]<br>
Output: 16<br>
Explanation: The perimeter is the 16 yellow stripes in the image above.<br>

## Example 2:<br>
Input: grid = [[1]]<br>
Output: 4<br>

## Example 3:<br>
Input: grid = [[1,0]]<br>
Output: 4<br>

# APPROACH:

- Traverse through the grid using nested loops.
- For each cell in the grid:
  - Check if it represents land (value is 1).
  - If it's land:
    - Add 4 to the total perimeter since each land cell contributes 4 to the perimeter.
    - Check if there's a land cell to the left (in the same row). If so, subtract 2 from the total perimeter, as the left edge is shared by two adjacent land cells.
    - Check if there's a land cell above (in the previous row). If so, subtract 2 from the total perimeter, as the top edge is shared by two adjacent land cells.
- Continue this process for all cells in the grid.
- Finally, return the total perimeter calculated.

## Time Complexity: O(row*col)
## Space Complexity: O(1)

# CODE:

```
class Solution {
public:
    int islandPerimeter(vector<vector<int>>& grid) {
        int res = 0;
        int row = grid.size();
        int col = grid[0].size();
        for(int i = 0; i<row; i++){
            for(int j = 0; j<col; j++){
                if(grid[i][j] == 1 ){
                    res = res + 4;
                    if(j>0 && grid[i][j-1] == 1)
                      res = res-2;
                    if(i>0 && grid[i-1][j] == 1){
                        res = res-2;
                    }
                }
                
            }
        }
        return res;
    }
};
```
