# ZOHO ROUND TWO QUESTIONS AND ANSWERS

# Problem 1: Greater on Right Side

### Problem Statement
You are given an array `Arr` of size `N`. Replace every element with the next greatest element (greatest element on its right side) in the array. Since there is no element next to the last element, replace it with `-1`.

### Example
#### Input:
```
N = 6
Arr[] = {16, 17, 4, 3, 5, 2}
```
#### Output:
```
17 5 5 5 2 -1
```
#### Explanation:
- For `16`, the greatest element on its right is `17`.
- For `17`, it's `5`.
- For `4`, it's `5`.
- For `3`, it's `5`.
- For `5`, it's `2`.
- For `2`, it's `-1` (no element to its right).

### Solution Code (Java)
```java
class Solution {
    public int[] replaceElements(int[] arr) {
        int mx = -1;
        for (int i = arr.length - 1; i >= 0; --i) {
            int x = arr[i];
            arr[i] = mx;
            mx = Math.max(mx, x);
        }
        return arr;
    }
}
```

### Time Complexity
- **O(N)**: Single traversal of the array.

### Space Complexity
- **O(N)**: To store the result.

---

# Problem 2: Modify Boolean Matrix

### Problem Statement
Given a Boolean matrix `mat[M][N]` of size `M x N`, modify it such that if a matrix cell `mat[i][j]` is `1` then make its adjacent cells as `0`.

### Example
#### Input:
```
1 0 1
0 1 0
1 1 1
```
#### Output:
```
0 0 0
0 0 0
1 0 1
```
#### Explanation:
- For the cell `mat[0][0]` which is `1`, its adjacent cells (`mat[0][1]` and `mat[1][0]`) are modified to `0`.
- For the cell `mat[1][1]` which is `1`, its adjacent cells (`mat[0][1]`, `mat[1][0]`, `mat[1][2]`, and `mat[2][1]`) are modified to `0`.
- The modification is not applied to the cell `mat[2][2]` as it doesn't have all four adjacent cells.

### Solution Code (Java)
```java
import java.util.*;

public class BooleanMatrixModifier {
    public static void main(String[] args) {
        int[][] mat = {
            {1, 0, 0, 1},
            {0, 0, 1, 0},
            {0, 1, 0, 0},
            {1, 0, 0, 0}
        };
        System.out.println("Original Matrix:");
        printMatrix(mat);
        modifyMatrix(mat);
        System.out.println("\nModified Matrix:");
        printMatrix(mat);
    }
    public static void modifyMatrix(int[][] mat) {
        int m = mat.length;
        int n = mat[0].length;
        int[][] temp = new int[m][n];
        for (int i = 0; i < m; i++) {
            System.arraycopy(mat[i], 0, temp[i], 0, n);
        }
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (mat[i][j] == 1) {
                    // Mark adjacent cells in the temp matrix
                    if (i > 0) temp[i - 1][j] = 0; // Up
                    if (i < m - 1) temp[i + 1][j] = 0; // Down
                    if (j > 0) temp[i][j - 1] = 0; // Left
                    if (j < n - 1) temp[i][j + 1] = 0; // Right
                }
            }
        }
        for (int i = 0; i < m; i++) {
            System.arraycopy(temp[i], 0, mat[i], 0, n);
        }
    }
    public static void printMatrix(int[][] mat) {
        for (int[] row : mat) {
            for (int cell : row) {
                System.out.print(cell + " ");
            }
            System.out.println();
        }
    }
}
```

### Time Complexity
- **O(M x N)**: Traverse all cells of the matrix.

### Space Complexity
- **O(M x N)**: Temporary matrix to store the original state.

---

# Problem 3:
### Problem Statement:
3. Equilibrium index of an array is an index such that the sum of elements at lower indexes is equal to the sum of elements at higher indexes. For example, in an array A:
### Example :
```
Input: A[] = {-7, 1, 5, 2, -4, 3, 0}
```
### Output:
``` 
3
```
#### Explanation:
- 3 is an equilibrium index, because:
- A[0] + A[1] + A[2] = A[4] + A[5] + A[6]
- Input: A[] = {1, 2, 3}
- Output: -1

### Solution Code (Java)
```Java

```

