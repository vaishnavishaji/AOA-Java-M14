# EX 4C Coin Change Problem - Dynamic Programming


## AIM:

To write a Java program to find the minimum number of coins required to make a given amount using the **Coin Change Dynamic Programming approach**.
If the given amount cannot be formed using the available denominations, return **-1**.

---

## Algorithm:

1. Read the coin denominations array and the target amount.
2. Create a DP array `dp[]` of size `amount + 1`, filled with a large value (amount + 1).
3. Set `dp[0] = 0` because 0 coins are needed to make amount 0.
4. For each amount `i` from 1 to `amount`, check each coin:

   * If `coin <= i`, update
     `dp[i] = min(dp[i], dp[i - coin] + 1)`
5. After filling the DP table:

   * If `dp[amount]` is still greater than amount, return **-1**.
   * Else return `dp[amount]`.
6. Print the result.

---

## Program:

```java
/*
Coin Change using Dynamic Programming
Developed by: Vaishnavi S.A
RegisterNumber:  212223220119
*/

import java.util.*;

public class Solution {
    public int coinChange(int[] coins, int amount) {
        int max = amount + 1;
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, max);
        dp[0] = 0;

        for (int i = 1; i <= amount; i++) {
            for (int coin : coins) {
                if (coin <= i) {
                    dp[i] = Math.min(dp[i], dp[i - coin] + 1);
                }
            }
        }
        return dp[amount] > amount ? -1 : dp[amount];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution solution = new Solution();

        String coinsLine = scanner.nextLine();
        String amountLine = scanner.nextLine();

        coinsLine = coinsLine.replaceAll("[^0-9,]", "");
        String[] coinsStr = coinsLine.split(",");
        int[] coins = new int[coinsStr.length];

        for (int i = 0; i < coinsStr.length; i++) {
            coins[i] = Integer.parseInt(coinsStr[i]);
        }

        int amount = Integer.parseInt(amountLine.replaceAll("[^0-9]", ""));
        int result = solution.coinChange(coins, amount);
        System.out.println(result);

        scanner.close();
    }
}
```

---

## Output:

<img width="601" height="357" alt="image" src="https://github.com/user-attachments/assets/04a38571-9a3c-4824-b424-592b48322b56" />


## Result:

The program was successfully implemented using Dynamic Programming, and the expected output was verified.

---
