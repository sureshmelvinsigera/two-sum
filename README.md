# Two Sum — Interviewer Guide

This is your cheat sheet. **Do not share this with the candidate.**

---

## Your Job

You're not trying to trick them. You're evaluating how they think, communicate, and write code under pressure. Be friendly but don't hand them the answer.

---

## How to Present the Problem

Read this out loud or share it on screen:

> "Given an array of integers and a target number, return the indices of the two numbers that add up to the target. You can assume there's exactly one solution, and you can't use the same element twice."

Then give them this example:

```
nums = [2, 7, 11, 15], target = 9
Expected output: [0, 1]
```

Don't give them more examples unless they ask. If they ask, use these:

```
nums = [3, 2, 4], target = 6 → [1, 2]
nums = [3, 3], target = 6 → [0, 1]
```

---

## What You're Looking For

#### Before They Code

- Do they ask clarifying questions? (Good sign.)
- Do they talk through a brute force approach first? (Good sign.)
- Do they jump straight into coding without a plan? (Red flag.)

#### While They Code

- Are they explaining their thinking or coding in silence? (Push them to talk.)
- Do they handle edge cases without being told? (Great sign.)
- Is their code clean and readable?

#### After They Code

- Can they walk through an example with their own code?
- Can they state the time and space complexity?
- Can they explain why their approach is better than brute force?

---

## The Answer Key

#### Brute Force (Acceptable, Not Great)

Two nested loops, check every pair. O(n²) time, O(1) space.

```python
def two_sum(nums, target):
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] + nums[j] == target:
                return [i, j]
```

#### Hash Map (What You Want to See)

One pass, store seen numbers, check for the complement. O(n) time, O(n) space.

```python
def two_sum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        partner = target - num
        if partner in seen:
            return [seen[partner], i]
        seen[num] = i
```

---

## Hints to Give (Only If They're Stuck)

Give these **one at a time**, wait at least 30 seconds between each.

1. "What if you already knew what number you were looking for? How would you calculate it?"
2. "Is there a data structure that lets you look something up in O(1) time?"
3. "What if you stored each number as you saw it, and checked before storing?"

If they need all three hints, that's okay — note how they respond to each one. Do they build on it or wait for the next one?

---

## Follow-Up Questions (If Time Allows)

Pick one or two of these after they solve it:

- "What if the array was already sorted? Could you solve it differently?"
- "What if there could be multiple valid pairs and you needed all of them?"
- "What if you had to find three numbers that add up to the target?"
- "What would break if you stored the number *before* checking for the partner?"

---

## Scoring Rubric

| Area | Strong | Okay | Needs Work |
|------|--------|------|------------|
| Communication | Talks through thinking clearly | Explains when asked | Codes in silence |
| Problem solving | Reaches hash map on their own | Gets there with 1 hint | Needs 3+ hints |
| Code quality | Clean, readable, no bugs | Minor issues, self-corrects | Messy or doesn't run |
| Complexity analysis | States both time and space | Gets time right, unsure on space | Can't explain either |
| Edge cases | Considers duplicates, negatives | Handles when prompted | Doesn't consider them |
