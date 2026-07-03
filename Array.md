# Two Sum II – Input Array Is Sorted

**Problem:** Given a **1-indexed sorted array**, return the indices of the two numbers such that they add up to the target.

---

## 🟠 Brute Force Approach

### Idea
- Check every possible pair of elements.
- If their sum equals the target, return their 1-based indices.

### Code

```javascript
var twoSum = function(nums, target) {
    let n = nums.length;

    for (let i = 0; i <= n - 2; i++) {
        for (let j = i + 1; j <= n - 1; j++) {
            if (nums[i] + nums[j] === target) {
                return [i + 1, j + 1];
            }
        }
    }

    return [-1, -1];
};
```

### Complexity

- **Time Complexity:** `O(n²)`
- **Space Complexity:** `O(1)`

> **Note:** This approach passes most test cases but **results in Time Limit Exceeded (TLE)** on large inputs because it checks every possible pair.

---

## 🟢 Optimal Approach (Two Pointers)

### Idea

Since the array is already **sorted**:

- Start one pointer from the beginning.
- Start another pointer from the end.
- If the sum is too small, move the left pointer.
- If the sum is too large, move the right pointer.
- If the sum equals the target, return the answer.

### Code

```javascript
var twoSum = function(nums, target) {
    let left = 0;
    let right = nums.length - 1;

    while (left < right) {
        let sum = nums[left] + nums[right];

        if (sum === target) {
            return [left + 1, right + 1];
        } else if (sum > target) {
            right--;
        } else {
            left++;
        }
    }

    return [-1, -1];
};
```

### Complexity

- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(1)`

✅ **Accepted** on LeetCode.

---

## Comparison

| Approach | Time Complexity | Space Complexity | Status |
|----------|-----------------|------------------|--------|
| Brute Force | `O(n²)` | `O(1)` | ❌ Time Limit Exceeded (TLE) |
| Two Pointers | `O(n)` | `O(1)` | ✅ Accepted |
