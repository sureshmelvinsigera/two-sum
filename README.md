# Two Sum

This is the most common coding interview question you'll encounter. If you can't solve this one confidently, stop and master it before moving on.

---

## The Problem

You're given a list of integers and a target number. Find the **two numbers** in the list that add up to the target, and return their **indices** (positions), not the numbers themselves.

There will always be exactly one valid answer, and you can't use the same element twice.

---

## Examples

#### Example 1

```
Input: nums = [2, 7, 11, 15], target = 9
Output: [0, 1]
```

Why? Because `nums[0] + nums[1]` is `2 + 7 = 9`.

#### Example 2

```
Input: nums = [3, 2, 4], target = 6
Output: [1, 2]
```

Why? Because `nums[1] + nums[2]` is `2 + 4 = 6`.

#### Example 3

```
Input: nums = [3, 3], target = 6
Output: [0, 1]
```

Why? Because `nums[0] + nums[1]` is `3 + 3 = 6`. Yes, duplicates can exist.

---

## Constraints

- The list has between 2 and 10,000 numbers.
- Each number can be anywhere from -1,000,000,000 to 1,000,000,000.
- The target follows the same range.
- There is always exactly one valid pair.

---

## Things to Think About Before You Code

- What's the simplest approach? What's its time complexity?
- Can you do better than checking every possible pair?
- What data structure lets you look things up fast?
- How do you make sure you don't use the same element twice?
- Are you returning **indices** or **values**? Read the problem again.

---

## Starter Code

```python
def two_sum(nums, target):
    # your code here
    pass
```

---

## How to Know You've Nailed It

- Your solution handles duplicates (Example 3).
- You can explain the time and space complexity of your approach.
- You can walk through an example out loud, step by step.
- You considered more than one approach and can explain why one is better.

Good luck.
