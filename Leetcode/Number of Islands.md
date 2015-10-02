```
public int numIslands(char[][] grid) {
    if (grid == null || grid.length == 0 || grid[0].length == 0) return 0;
    int count = 0;
    for (int i = 0; i < grid.length; i++) {
        for (int j = 0; j < grid[0].length; j++) {
            if (grid[i][j] != '1') continue;
            else {
                count++;
                floodFill(grid, i, j);
            }
        }
    }
    return count;
}

public void floodFill(char[][] grid, int i, int j) {
    if (i < 0 || i >= grid.length || j < 0 || j >= grid[0].length) return;
    if (grid[i][j] != '1') return; // either 0(water) or 2(visited)
    grid[i][j] = '2';
    floodFill(grid, i - 1, j);
    floodFill(grid, i + 1, j);
    floodFill(grid, i, j - 1);
    floodFill(grid, i, j + 1);
}
```
