# EX 4E Longest Increasing Subsequence – Dynamic Programming


## AIM:

To write a Java program to compute the length of the **Longest Increasing Subsequence (LIS)** in a given integer array using **Dynamic Programming**.

---

## Algorithm:

1. Read the array size `n` and the array elements.
2. Create a DP array `dp[]` of size `n`, initialized with 1 (each number is an LIS of length 1).
3. For each index `i` from 1 to n−1:

   * Check previous elements `j` from 0 to i−1.
   * If `nums[i] > nums[j]`, update
     `dp[i] = max(dp[i], dp[j] + 1)`
4. Find the maximum value in the DP array — this is the LIS length.
5. Print the result.

---

## Program:

```java
/*
Program to implement Reverse a String
Developed by: Vaishnavi S.A
RegisterNumber:  212223220119
*/

import java.util.*;

public class LongestIncreasingSubsequence {
    public static int lengthOfLIS(int[] nums) {
        int[] dp = new int[nums.length];
        Arrays.fill(dp, 1);

        for (int i = 1; i < nums.length; i++) {
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
        }

        int longest = 0;
        for (int c : dp) {
            longest = Math.max(longest, c);
        }
        return longest;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }

        int result = lengthOfLIS(nums);
        System.out.println("Length of Longest Increasing Subsequence: " + result);

        scanner.close();
    }
}
```

---

## Output:

<img width="1203" height="282" alt="image" src="https://github.com/user-attachments/assets/84789017-ea66-4602-b337-e272c483b622" />

---

## Result:

The program was successfully implemented using Dynamic Programming and the expected output was verified.

---
