# 1523. Count Odd Numbers in an Interval Range

Class: Programming Skills - LeetCode
Created: April 23, 2022 2:00 PM
Link to Problem: https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/
Property: No
Serial Number: Yes
Type: Coding

## Problem Description

> Given two non-negative integers `low`and `high`. Return the *count of odd numbers between* `low` *and* `high` *(inclusive)*.
> 
- Problem Link: [https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/](https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/)

![Capture.PNG](1523%20Count%20Odd%20Numbers%20in%20an%20Interval%20Range%20776a4a3c706448aaacefa4462ebb3e3b/Capture.png)

## Solution Approaches

### Approach 1:

The simple solution at comes to mind first would be to loop through from `low` to `high` and check which numbers yield a different result when divided by 2 → 

- **Note:** If the modulo operator yields 1, in that case the number is odd and should be counted.

A simple code should be able to do this for us, eh?

![Figure 1: Naive Code](1523%20Count%20Odd%20Numbers%20in%20an%20Interval%20Range%20776a4a3c706448aaacefa4462ebb3e3b/Untitled.png)

Figure 1: Naive Code

Too simple? Where’s the catch? Time Limit Exceeded (TLE) -

![Figure 2: Submission result of ‘Naive Code’](1523%20Count%20Odd%20Numbers%20in%20an%20Interval%20Range%20776a4a3c706448aaacefa4462ebb3e3b/Untitled%201.png)

Figure 2: Submission result of ‘Naive Code’

Let’s see why this happened. This would take `O(n)` travelling from left to right and checking if each number is odd or not. So, if the input values from `low = 0` and `high = 100000000` or $10^9$. This would lead to looping through a very large set of input and the checker would give up.

What’s a better way to go about solving this problem? Let’s get outsmart the TLE!

### Approach 2:

Let’s concentrate on the fact that in a given range, there will be almost half odd numbers. Let’s take care of the corner cases with this thought in mind. What are the possible scenarios?

**Scenario 1:** `[even, even] → [2, 3, 4, 5, 6]`, by using high level of human intelligence we can clearly see that between `2 and 6` there will be `2` odd numbers. 

**Scenario 2:** `[even, odd] → [2, 3, 4, 5, 6, 7]`, again summoning our intelligence we can say that there will be `3` odd numbers in this range.

**Scenario 3:** `[odd, even] → [1, 2, 3, 4, 5, 6]`, calling up our super brain capability we can count that there will be `3` odd numbers in this range.

**Scenario 4:** `[odd, odd] → [1, 2, 3, 4, 5]`, c’mon this should be no brainer now 😛 there are `3` odd numbers.

What can we conclude from this?

**From Scenario 1:** If the numbers are even then we can simply take the difference and divide it by 2 → $(high - low)/2$  to get the odd numbers count in between.

Extrapolating on the previously presented Scenario: `[2, 3, 4, 5, 6, 7, 8]` → $(8-2)/2 = 3$

**From Scenario 2-4:** If any one of the numbers are odd, there will be 1 extra number always classified as odd. Hence, $(high-low)/2 + 1$. 

**Note:** treating the division to be of integer numbers yielding an integer as a result

`[even, odd] → [2, 3, 4, 5, 6, 7]` → $(7-2)/2 + 1 = 3$

`[odd, even] → [1, 2, 3, 4, 5, 6]` → $(6-1)/2 + 1 = 3$

`[odd, odd] → [1, 2, 3, 4, 5]` → $(5-1)/2 + 1 = 3$

In this we did not have to loop around the numbers to find the result, just a basic subtraction, division and addition of the numbers already available to us would be enough to sail through. A simple realisation at times takes us places, eh? Let’s code it up!

![Figure 3: Optimized Code](1523%20Count%20Odd%20Numbers%20in%20an%20Interval%20Range%20776a4a3c706448aaacefa4462ebb3e3b/Untitled%202.png)

Figure 3: Optimized Code

Found it elegant yet? If no, 

![Untitled](1523%20Count%20Odd%20Numbers%20in%20an%20Interval%20Range%20776a4a3c706448aaacefa4462ebb3e3b/Untitled%203.png)
