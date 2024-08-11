### 01. 959. Regions Cut By Slashes:
**An n x n grid is composed of 1 x 1 squares where each 1 x 1 square consists of a '/', '\', or blank space ' '. These characters divide the square into contiguous regions.**
**Given the grid grid represented as a string array, return the number of regions.**
**Note that backslash characters are escaped, so a '\' is represented as '\\'.**

### using C++
```
class Solution {
    vector<int> parent;
    vector<int> rank;
    int count;
    
public:
    int regionsBySlashes(vector<string>& grid) {
        int n = grid.size();
        int dots = n + 1;
        parent.resize(dots * dots);
        rank.resize(dots * dots, 1);
        count = 0;

        // Initialize Union-Find structure
        for (int i = 0; i < parent.size(); ++i) {
            parent[i] = i;
        }

        // Connect boundaries to the top-left corner (0,0)
        for (int i = 0; i < dots; ++i) {
            for (int j = 0; j < dots; ++j) {
                if (i == 0 || j == 0 || i == n || j == n) {
                    int cell = i * dots + j;
                    unionSets(0, cell);
                }
            }
        }

        // Process each cell and connect regions based on slashes
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (grid[i][j] == '\\') {
                    int cell1 = i * dots + j;
                    int cell2 = (i + 1) * dots + (j + 1);
                    unionSets(cell1, cell2);
                } else if (grid[i][j] == '/') {
                    int cell1 = (i + 1) * dots + j;
                    int cell2 = i * dots + (j + 1);
                    unionSets(cell1, cell2);
                }
            }
        }

        return count;
    }
    
private:
    void unionSets(int a, int b) {
        int parentA = find(a);
        int parentB = find(b);
        if (parentA == parentB) {
            count++;
        } else {
            if (rank[parentA] > rank[parentB]) {
                parent[parentB] = parentA;
            } else if (rank[parentA] < rank[parentB]) {
                parent[parentA] = parentB;
            } else {
                parent[parentB] = parentA;
                rank[parentA]++;
            }
        }
    }
    
    int find(int a) {
        if (parent[a] == a) {
            return a;
        }
        return parent[a] = find(parent[a]);
    }
};
```

### 02. 1568. Minimum Number of Days to Disconnect Island:
**You are given an m x n binary grid grid where 1 represents land and 0 represents water. An island is a maximal 4-directionally (horizontal or vertical) connected group of 1's.**
**The grid is said to be connected if we have exactly one island, otherwise is said disconnected.**
**In one day, we are allowed to change any single land cell (1) into a water cell (0).**
**Return the minimum number of days to disconnect the grid.**

### using java

```
class Solution {
    public int minDays(int[][] grid) {
        if (countIslands(grid) != 1) return 0;

        for (int i = 0; i < grid.length; i++) {
            for (int j = 0; j < grid[0].length; j++) {
                if (grid[i][j] == 1) {
                    grid[i][j] = 0;
                    if (countIslands(grid) != 1) return 1;
                    grid[i][j] = 1;
                }
            }
        }

        return 2;
    }

    private int countIslands(int[][] grid) {
        boolean[][] seen = new boolean[grid.length][grid[0].length];
        int islands = 0;

        for (int i = 0; i < grid.length; i++) {
            for (int j = 0; j < grid[0].length; j++) {
                if (grid[i][j] == 1 && !seen[i][j]) {
                    islands++;
                    dfs(grid, i, j, seen);
                }
            }
        }
        return islands;
    }

    private void dfs(int[][] grid, int r, int c, boolean[][] seen) {
        seen[r][c] = true;
        int[][] directions = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};
        for (int[] dir : directions) {
            int nr = r + dir[0], nc = c + dir[1];
            if (nr >= 0 && nr < grid.length && nc >= 0 && nc < grid[0].length && grid[nr][nc] == 1 && !seen[nr][nc]) {
                dfs(grid, nr, nc, seen);
            }
        }
    }
}
```


