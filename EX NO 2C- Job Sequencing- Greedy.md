# EX 1C Job Sequencing using Greedy Approach

## AIM:

To write a Java program to for given constraints.
Given an integer array nums and an integer k, return the number of pairs (i, j) where i < j such that |nums[i] - nums[j]| == k.

The value of |x| is defined as:

x if x >= 0.
-x if x < 0.You're given N jobs, each with:

A unique jobId

A deadline (by which it must be completed)

A profit (earned only if completed on or before the deadline)

Each job:

Takes exactly 1 unit of time

Only one job can be done at a time

Your goal is to maximize total profit while completing the maximum number of jobs possible within their deadlines.

## Algorithm

1. Sort all jobs in **descending order of profit** (greediest approach wins).
2. Find the maximum deadline to know how many time slots are available.
3. Create an array of time slots, initially empty.
4. For each job in sorted order, try placing it in the **latest free slot** before or on its deadline.
5. Count all scheduled jobs and sum their profit — return both.

#### Developed By: VIDHIYA LAKSHMI S

#### Register Number: 212223230238

## Program:

### to implement job sequencing

```java
import java.util.Arrays;

class Job {
    int id, deadline, profit;
    Job(int id, int deadline, int profit) {
        this.id = id;
        this.deadline = deadline;
        this.profit = profit;
    }
}

public class Main {

    public static int[] jobScheduling(Job[] jobs) {
        Arrays.sort(jobs, (a, b) -> b.profit - a.profit);

        int maxDeadline = 0;
        for (Job j : jobs) {
            maxDeadline = Math.max(maxDeadline, j.deadline);
        }

        int[] slots = new int[maxDeadline + 1];
        Arrays.fill(slots, -1);

        int jobCount = 0;
        int totalProfit = 0;

        for (Job j : jobs) {
            for (int t = j.deadline; t > 0; t--) {
                if (slots[t] == -1) {
                    slots[t] = j.id;
                    jobCount++;
                    totalProfit += j.profit;
                    break;
                }
            }
        }

        return new int[]{jobCount, totalProfit};
    }

    public static void main(String[] args) {
        Job[] jobs = {
            new Job(1, 4, 20),
            new Job(2, 1, 10),
            new Job(3, 1, 40),
            new Job(4, 1, 30)
        };

        int[] result = jobScheduling(jobs);
        System.out.println("Jobs done: " + result[0]);
        System.out.println("Total profit: " + result[1]);
    }
}
```

## Output:

```
Jobs done: 2
Total profit: 60
```

## Result:

The program successfully implemented and the expected output is verified.
