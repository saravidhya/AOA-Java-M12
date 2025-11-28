# EX 2B Jump Game using Greedy Algorithm.

## AIM:

To write a Java program to for given constraints.
You are given an array of integers. Each number represents the maximum number of steps you can jump forward from that position.

You start from the first element (index 0).
Write a program to find the minimum number of jumps required to reach the last index of the array.

If it is not possible to reach the end, return -1.

## Algorithm

1. If the array has only one element, you're already at the end — return 0.
2. Maintain three variables:
   - `jumps` (how many jumps taken),
   - `currentEnd` (end of current jump range),
   - `farthest` (farthest index you can reach so far).
3. Loop through the array (except the last element), updating `farthest` to the maximum reachable index.
4. When you reach `currentEnd`, you must “jump,” so increment `jumps` and update `currentEnd` to `farthest`.
5. If you ever cannot move forward (farthest ≤ current index), return `-1`. Otherwise, return `jumps`.

#### Developed By: VIDHIYA LAKSHMI S

#### Register Number: 212223230238

## Program:

### to implement jump game
```java
public class Main {

    public static int minJumps(int[] nums) {
        if (nums.length <= 1) return 0;

        int jumps = 0;
        int currentEnd = 0;
        int farthest = 0;

        for (int i = 0; i < nums.length - 1; i++) {
            farthest = Math.max(farthest, i + nums[i]);

            if (i == currentEnd) {
                jumps++;
                currentEnd = farthest;

                if (currentEnd <= i) {
                    return -1;
                }
            }
        }
        return jumps;
    }

    public static void main(String[] args) {
        int[] nums = {2, 3, 1, 1, 4};
        System.out.println("Minimum jumps to reach end: " + minJumps(nums));
    }
}
```

## Output:

```
Minimum jumps to reach end: 2
```

## Result:

The program successfully implemented and the expected output is verified.
