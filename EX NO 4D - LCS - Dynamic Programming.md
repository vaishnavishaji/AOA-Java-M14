# EX 4D Longest Common SubSequence - Dynamic Programming


## AIM:

To write a Java program to find the length of the **Longest Common Subsequence (LCS)** between two given strings using **Dynamic Programming**.

---

## Algorithm:

1. Read the two input strings `text1` and `text2`.
2. Create a 2D DP matrix `dp[m+1][n+1]` where `m` and `n` are the lengths of the strings.
3. Fill the DP table from bottom-right to top-left:

   * If characters match:
     `dp[i][j] = 1 + dp[i+1][j+1]`
   * Else:
     `dp[i][j] = max(dp[i+1][j], dp[i][j+1])`
4. The value at `dp[0][0]` gives the length of the LCS.
5. Print the result.

---

## Program:

```java
/*
Program to implement Longest Common SubSequence
Developed by: Vaishnavi S.A
RegisterNumber:  212223220119
*/

import java.util.Scanner;

public class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int[][] dpGrid = new int[text1.length() + 1][text2.length() + 1];

        for (int col = text2.length() - 1; col >= 0; col--) {
            for (int row = text1.length() - 1; row >= 0; row--) {
                if (text1.charAt(row) == text2.charAt(col)) {
                    dpGrid[row][col] = 1 + dpGrid[row + 1][col + 1];
                } else {
                    dpGrid[row][col] = Math.max(dpGrid[row + 1][col], dpGrid[row][col + 1]);
                }
            }
        }
        return dpGrid[0][0];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        String text1 = sc.nextLine().replaceAll("\"", "");
        String text2 = sc.nextLine().replaceAll("\"", "");

        int lcsLength = sol.longestCommonSubsequence(text1, text2);
        System.out.println("Length of Longest Common Subsequence: " + lcsLength);

        sc.close();
    }
}
```

---

## Output:

<img width="1152" height="297" alt="image" src="https://github.com/user-attachments/assets/43c9f0ba-d6fe-4de2-9777-310b89646bd1" />

---

## Result:

The program was successfully implemented using Dynamic Programming and the expected output was verified.
