# EX 2D Pattern Matching using Naive Approach.

## AIM:

To write a Java program to for given constraints.
Given text string with length n and a pattern with length m, the task is to prints all occurrences of pattern in text.
Note: You may assume that n > m.

Examples:

Input: text = "THIS IS A TEST TEXT", pattern = "TEST"
Output: Pattern found at index 10

Input: text = "AABAACAADAABAABA", pattern = "AABA"
Output: Pattern found at index 0, Pattern found at index 9, Pattern found at index 12

## Algorithm

1. Read the text and pattern; let `n` be text length and `m` be pattern length.
2. Loop through text from index `0` to `n - m`.
3. For each index, compare the next `m` characters with the pattern.
4. If all characters match, record the index as an occurrence.
5. Print all found indices (or nothing if no match exists).

#### Developed By: VIDHIYA LAKSHMI S

#### Register Number: 212223230238

## Program:

### to implement pattern matching

```java
public class Main {

    public static void searchPattern(String text, String pattern) {
        int n = text.length();
        int m = pattern.length();

        for (int i = 0; i <= n - m; i++) {
            int j;
            for (j = 0; j < m; j++) {
                if (text.charAt(i + j) != pattern.charAt(j)) {
                    break;
                }
            }
            if (j == m) {
                System.out.println("Pattern found at index " + i);
            }
        }
    }

    public static void main(String[] args) {
        String text = "AABAACAADAABAABA";
        String pattern = "AABA";

        searchPattern(text, pattern);
    }
}
```

## Output:

```
Pattern found at index 0
Pattern found at index 9
Pattern found at index 12
```

## Result:

The program successfully implemented and the expected output is verified.
