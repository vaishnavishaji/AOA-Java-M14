# EX 4A Kadane's Algorithm - Dynamic Programming

## AIM:

To write a Java program to compute the maximum net energy that can be collected from any contiguous block of buildings arranged in a circular grid using **Kadane’s Algorithm**.

The buildings either generate or consume energy. Since the grid is circular, the maximum subarray sum may wrap around the end to the beginning.

---

## Algorithm:

1. Read the number of buildings `n` and the net energy values.
2. Use **Kadane’s Algorithm** to find the maximum subarray sum (non-circular case).
3. Use **Kadane’s Algorithm (inverted)** to find the minimum subarray sum.
4. Compute the total sum of all energy values.
5. If all values are negative, return the maximum value directly.
6. Otherwise, compute the maximum circular sum as
   `totalSum - minSum`.
7. The answer is the maximum of:

   * Normal maximum subarray sum
   * Circular maximum subarray sum
8. Print the result.

---

## Program:

```java
/*
Kadane's Algorithm
Developed by: Vaishnavi S.A
RegisterNumber:  212223220119
*/

import java.util.*;

public class SolarEnergyMaximizer {

    public static int maxCircularEnergy(int[] energy) {
        int totalSum = 0;
        int maxSum = energy[0];
        int currMax = energy[0];
        int minSum = energy[0];
        int currMin = energy[0];

        for (int i = 1; i < energy.length; i++) {
            int val = energy[i];
            currMax = Math.max(val, currMax + val);
            maxSum = Math.max(maxSum, currMax);

            currMin = Math.min(val, currMin + val);
            minSum = Math.min(minSum, currMin);

            totalSum += val;
        }
        totalSum += energy[0];

        if (maxSum < 0) return maxSum;
        return Math.max(maxSum, totalSum - minSum);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] energy = new int[n];
        for (int i = 0; i < n; i++) {
            energy[i] = sc.nextInt();
        }
        System.out.println(maxCircularEnergy(energy));
    }
}
```

---

## Output:

<img width="858" height="273" alt="image" src="https://github.com/user-attachments/assets/ae9d6938-7e5f-4e86-8c66-afafdd877030" />

---

## Result:

The program was successfully implemented using Kadane’s Algorithm and the output was verified.
