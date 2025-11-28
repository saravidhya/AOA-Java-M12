# EX 2E Pattern Matching using KMP Algorithm.

## AIM:

To write a Java program for the following constraints.
Longest Palindromic Substring
Given a string s, return the longest palindromic substring in s.
using Manacher's Algorithm

## Algorithm

1. Transform the string by inserting separators (like `#`) between characters to handle even/odd palindromes uniformly.
2. Create an array `P[]` where `P[i]` stores the radius of the palindrome centered at position `i`.
3. Use two pointers, `center` and `right`, to track the rightmost palindrome seen so far and expand around centers efficiently.
4. Update `P[i]` using mirror values and expand around `i` when possible.
5. Convert the best center and radius back to the original string and return the longest palindromic substring.

#### Developed By: VIDHIYA LAKSHMI S

#### Register Number: 212223230238

## Program:

### to implement manachers algorithm

```java
public class Main {

    public static String longestPalindrome(String s) {
        if (s == null || s.length() == 0) return "";

        String t = preprocess(s);
        int n = t.length();
        int[] P = new int[n];
        int center = 0, right = 0;

        for (int i = 1; i < n - 1; i++) {
            int mirror = 2 * center - i;

            if (i < right) {
                P[i] = Math.min(right - i, P[mirror]);
            }

            while (t.charAt(i + 1 + P[i]) == t.charAt(i - 1 - P[i])) {
                P[i]++;
            }
            if (i + P[i] > right) {
                center = i;
                right = i + P[i];
            }
        }

        int maxLen = 0;
        int centerIndex = 0;
        for (int i = 1; i < n - 1; i++) {
            if (P[i] > maxLen) {
                maxLen = P[i];
                centerIndex = i;
            }
        }

        int start = (centerIndex - maxLen) / 2;
        return s.substring(start, start + maxLen);
    }

    private static String preprocess(String s) {
        StringBuilder sb = new StringBuilder("^");
        for (char c : s.toCharArray()) {
            sb.append('#').append(c);
        }
        sb.append("#$");
        return sb.toString();
    }

    public static void main(String[] args) {
        String s = "babad";
        System.out.println("Longest Palindromic Substring: " + longestPalindrome(s));
    }
}
```

## Output:

```
Longest Palindromic Substring: bab
```

## Result:

The program successfully implemented and the expected output is verified.
