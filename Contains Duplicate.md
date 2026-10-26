# Contains Duplicate

> **Problem Link:** [LeetCode 217 - Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)
> **Pattern:** Hash Set | **Difficulty:** Easy | **Key Idea:** Value-to-presence lookup via hashing

---

### 📌 Problem Description
Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is **distinct**.

---

### 💡 Intuition & Progression

1. **Brute Force (Exhaustive Search):**
   * *Thought:* Compare every number with every other number.
   * *Why it's bad:* Checking all pairs requires nested loops, causing `O(n²)` time—too slow for large inputs (10⁵).

2. **Sorting (Bring Identicals Together):**
   * *Thought:* If duplicates exist, sorting the array will force them to sit next to each other.
   * *Trade-off:* Reduces time to `O(n log n)` and takes `O(1)` extra space, but mutates the original array and is slower than linear time.

3. **Hash Set (Memory for Speed - Optimal):**
   * *Thought:* As we scan through, "remember" what we've already seen.
   * *The "Aha!":* A Hash Set provides average `O(1)` lookup and insertion. The very first time we see an element that's already in the set, we stop and return `true`.

---

### ⚡ Approaches & Trade-offs

| Approach | Time | Space | Pros / Cons |
| :--- | :--- | :--- | :--- |
| **1. Brute Force** | `O(n²)` | `O(1)` | No extra memory, but leads to Time Limit Exceeded (TLE). |
| **2. Sorting** | `O(n log n)` | `O(1)`* | Saves memory, but mutates the input array (`nums`). |
| **3. Hash Set** | `O(n)` | `O(n)` | Fastest runtime; trades `O(n)` space for instant duplicate detection. |

*\*Note: Sorting achieves `O(1)` auxiliary space only if in-place mutation is permitted by the caller; otherwise `O(n)` to clone.*

---

### 📝 Pseudo Code

```text
// 1. Brute Force
for i = 0 to n - 1:
    for j = i + 1 to n - 1:
        if nums[i] == nums[j]:
            return true
return false

// 2. Sorting
sort(nums)
for i = 0 to n - 2:
    if nums[i] == nums[i + 1]:
        return true
return false

// 3. Hash Set (Optimal)
seen = empty HashSet
for num in nums:
    if num in seen:
        return true
    seen.add(num)
return false
