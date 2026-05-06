# Two Sum — The Classic First Interview Question

This is literally the most popular coding interview question on the planet. If you see it in an interview, treat it as a gift.

---

## What the Problem is Asking

You get a list of numbers and a target number. Find the **two numbers** in the list that add up to the target, then return their **positions** (indices), not the numbers themselves.

That's it. That's the whole problem.

#### Quick Example

List: `[2, 7, 11, 15]`, Target: `9`

Ask yourself: which two numbers add up to 9? **2 + 7 = 9**. They sit at index 0 and index 1, so you return `[0, 1]`.

---

## The Brute Force Way (Works, But Slow)

#### The Idea

Check every possible pair. Try nums[0] with nums[1], then nums[0] with nums[2], and so on until you find the pair that hits the target.

#### Why It Works

You're literally checking everything. You will always find the answer.

#### Why Interviewers Won't Love It

It's O(n²) time. Two nested loops. For a small list, fine. For 10,000 elements, that's up to ~100 million checks. You can mention this approach, but immediately follow up with the better one below.

```python
def two_sum(nums, target):
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] + nums[j] == target:
                return [i, j]
```

---

## The Hash Map Way (What They Actually Want to Hear)

#### The Key Insight

If you're looking at a number and the target is 9, you don't need to search the whole list for its partner. You already **know** what the partner has to be.

Looking at `2` with target `9`? The partner **must** be `9 - 2 = 7`. That's just subtraction.

So the real question becomes: "Have I already seen a 7?"

#### The Plan

1. Walk through the list one number at a time.
2. For each number, calculate what its partner would need to be (`target - current number`).
3. Check if that partner is already in your hash map.
4. If yes, you're done. Return both indices.
5. If no, store the current number and its index in the hash map and move on.

#### Walk Through It

List: `[2, 7, 11, 15]`, Target: `9`, Hash map starts empty: `{}`

| Step | Current Number | I Need... | In the Map? | Action |
|------|---------------|-----------|-------------|--------|
| 1 | 2 | 9 - 2 = 7 | No | Store `{2: 0}` |
| 2 | 7 | 9 - 7 = 2 | Yes, at index 0 | Return `[0, 1]` |

Done in 2 steps instead of looping through everything.

#### The Code

```python
def two_sum(nums, target):
    seen = {}  # number -> index

    for i, num in enumerate(nums):
        partner = target - num

        if partner in seen:
            return [seen[partner], i]

        seen[num] = i
```

#### Why This is Better

- **Time:** O(n) — you walk through the list once. Hash map lookups are O(1).
- **Space:** O(n) — you're storing numbers in the map. This is the trade-off.

---

## Things That Trip People Up

#### "Why not sort the list first?"
You could, and there's a valid two-pointer approach for that. But sorting scrambles the original indices, so you'd need to track them separately. The hash map approach is cleaner for this problem.

#### "What if there are duplicate numbers?"
It still works. Look at `[3, 3]` with target `6`. When you hit the second `3`, the first `3` is already in your map. You return their indices. The hash map only stores the most recent index for a number, but since you check *before* you store, you catch the pair in time.

#### "Can I use the same element twice?"
No. The problem says you can't. But the hash map approach naturally avoids this because you check for the partner *before* adding the current number to the map.

---

## What to Say in the Interview

1. **Start by clarifying** — "So I'm returning indices, not the values themselves, right?" (Shows you read carefully.)
2. **Mention brute force first** — "The naive approach is O(n²) with two loops, but we can do better."
3. **Explain the hash map idea in words before coding** — "I can use a hash map to remember what I've seen, and for each number just check if its complement exists."
4. **Write the code.**
5. **State the complexity** — "This is O(n) time and O(n) space."

---

## Complexity Cheat Sheet

| Approach | Time | Space |
|----------|------|-------|
| Brute Force (two loops) | O(n²) | O(1) |
| Hash Map (one pass) | O(n) | O(n) |

---

## Bottom Line

The pattern here — **"use a hash map to remember what you've seen"** — shows up constantly in interview problems. Master it on this easy problem so it becomes second nature when you see it in harder ones.
