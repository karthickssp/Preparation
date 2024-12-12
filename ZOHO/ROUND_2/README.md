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

### Solution Code (C++)
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> replaceWithGreatest(vector<int> &arr) {
    int n = arr.size();
    vector<int> result(n);
    int maxFromRight = -1;

    for (int i = n - 1; i >= 0; --i) {
        result[i] = maxFromRight;
        maxFromRight = max(maxFromRight, arr[i]);
    }
    return result;
}

int main() {
    vector<int> arr = {16, 17, 4, 3, 5, 2};
    vector<int> result = replaceWithGreatest(arr);

    for (int x : result) {
        cout << x << " ";
    }
    return 0;
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

### Solution Code (C++)
```cpp
#include <iostream>
#include <vector>
using namespace std;

void modifyMatrix(vector<vector<int>> &mat) {
    int M = mat.size();
    int N = mat[0].size();
    vector<vector<int>> temp = mat;

    for (int i = 0; i < M; ++i) {
        for (int j = 0; j < N; ++j) {
            if (temp[i][j] == 1) {
                if (i > 0) mat[i - 1][j] = 0;
                if (i < M - 1) mat[i + 1][j] = 0;
                if (j > 0) mat[i][j - 1] = 0;
                if (j < N - 1) mat[i][j + 1] = 0;
            }
        }
    }
}

int main() {
    vector<vector<int>> mat = {
        {1, 0, 1},
        {0, 1, 0},
        {1, 1, 1}
    };

    modifyMatrix(mat);

    for (const auto &row : mat) {
        for (int x : row) {
            cout << x << " ";
        }
        cout << endl;
    }
    return 0;
}
```

### Time Complexity
- **O(M x N)**: Traverse all cells of the matrix.

### Space Complexity
- **O(M x N)**: Temporary matrix to store the original state.

---

### Summary
Both problems focus on manipulating arrays/matrices based on specific rules, ensuring efficient traversal and modifications. The solutions provided are optimized for time and space while adhering to the constraints.
