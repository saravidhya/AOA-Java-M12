# EX 2A Assign Cookies using Greedy Algorithm.

## AIM:

To Write a Java program for the following Constraints.
Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie.

Each child i has a greed factor g[i], which is the minimum size of a cookie that the child will be content with; and each cookie j has a size s[j]. If s[j] >= g[i], we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximise the number of your content children and output the maximum number.

## Algorithm

1. Sort the greed array `g` and the cookie sizes array `s`.
2. Use two pointers: one for children, one for cookies.
3. If the current cookie satisfies the current child (s[j] ≥ g[i]), give it and move both pointers.
4. Otherwise, try a bigger cookie by moving the cookie pointer forward.
5. Continue until one list is exhausted and return the number of satisfied children.

#### Developed By: VIDHIYA LAKSHMI S

#### Register Number: 212223230238

## Program:

### to implement greedy assign cookies

```java
import java.util.Arrays;

public class Main {

    public static int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);

        int i = 0; // child pointer
        int j = 0; // cookie pointer
        int content = 0;

        while (i < g.length && j < s.length) {
            if (s[j] >= g[i]) {
                content++;
                i++;
                j++;
            } else {
                j++;
            }
        }
        return content;
    }

    public static void main(String[] args) {
        int[] g = {1, 2, 3};
        int[] s = {1, 1};

        System.out.println("Maximum content children: " + findContentChildren(g, s));
    }
}
```

## Output:

```
Maximum content children: 1
```

## Result:

The program successfully print all the numbers from 1 to N.
