# EX 4B Frog Jump - Dynamic Programming

## AIM:

To write a Java program for the given constraints to compute the number of distinct ways a frog can reach the n-th step by jumping either 1 or 2 steps at a time.

The solution must be implemented using **Dynamic Programming**.

---

## Algorithm:

1. Read the value of `n` (number of steps).
2. If `n` is 0 or 1, return 1 (only one way).
3. Create an array `dp[]` of size `n + 1`.
4. Initialise `dp[0] = 1` and `dp[1] = 1`.
5. For each step from 2 to n, compute:
   `dp[i] = dp[i − 1] + dp[i − 2]`
6. The final answer is stored in `dp[n]`.
7. Print the result.

---

## Program:

```java
/*
Frog Jump
Developed by: Vaishnavi S.A
RegisterNumber:  212223220119
*/

import java.util.Scanner;

public class FrogJump {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        scanner.close();
        System.out.println(countWays(n));
    }

    public static int countWays(int n) {
        if (n <= 1) return 1;
        int[] dp = new int[n + 1];
        dp[0] = 1;
        dp[1] = 1;
        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        return dp[n];
    }
}
```

---

## Output:

<img width="516" height="245" alt="image" src="https://github.com/user-attachments/assets/ce873ee1-d03e-41aa-9960-d13896c3d00a" />

---

## Result:

The program was successfully implemented using Dynamic Programming and the expected output was verified.
