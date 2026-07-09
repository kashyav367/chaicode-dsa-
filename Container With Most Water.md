# LeetCode 11 – Container With Most Water

Given `n` non-negative integers `height[0], height[1], ..., height[n-1]`, where each represents a point at coordinate `(i, height[i])`, find two lines that, together with the x-axis, form a container that holds **the most water**.

Return **the maximum amount of water** a container can store.

> **Note:** You may not slant the container — it must be vertical lines.

---

# 🟠 Brute Force Approach

## 💡 Idea

* Try every possible pair of lines `(i, j)`.
* For each pair, the water stored is bounded by the **shorter** of the two lines.
* Area = `min(height[i], height[j]) * (j - i)`.
* Keep track of the maximum area found.

---

## 📝 Pseudocode

```text
Set maxArea = 0

For i from 0 to n-2
    For j from i+1 to n-1

        currentHeight = min(height[i], height[j])
        currentWidth = j - i
        currentArea = currentHeight * currentWidth

        If currentArea > maxArea
            maxArea = currentArea

Return maxArea
```

---

## 💻 JavaScript

```javascript
var maxArea = function(height) {
    let maxArea = 0;
    const n = height.length;

    for (let i = 0; i < n - 1; i++) {
        for (let j = i + 1; j < n; j++) {

            const currentHeight = Math.min(height[i], height[j]);
            const currentWidth = j - i;
            const currentArea = currentHeight * currentWidth;

            if (currentArea > maxArea) {
                maxArea = currentArea;
            }
        }
    }

    return maxArea;
};
```

---

## ⏱ Complexity

* **Time Complexity:** `O(n²)`
* **Space Complexity:** `O(1)`

> **Note:** Correct but too slow for large inputs — checks every pair even when it's obviously not optimal.

---

# 🟢 Optimal Approach (Two Pointers)

## 💡 Idea

* Start with two pointers at the extreme ends of the array.
* Compute the area formed by the two pointers.
* Always move the pointer pointing to the **shorter** line inward — moving the taller one can never increase the area, since the shorter line still caps the height.
* Keep updating the maximum area as the pointers move.

---

## 📝 Pseudocode

```text
left = 0
right = n - 1
maxArea = 0

While left < right

    currentHeight = min(height[left], height[right])
    currentWidth = right - left
    currentArea = currentHeight * currentWidth

    maxArea = max(maxArea, currentArea)

    If height[left] < height[right]
        left++
    Else
        right--

Return maxArea
```

---

## 💻 JavaScript

```javascript
var maxArea = function(height) {

    let left = 0;
    let right = height.length - 1;
    let maxArea = 0;

    while (left < right) {

        const currentHeight = Math.min(height[left], height[right]);
        const currentWidth = right - left;
        const currentArea = currentHeight * currentWidth;

        maxArea = Math.max(maxArea, currentArea);

        if (height[left] < height[right]) {
            left++;
        } else {
            right--;
        }
    }

    return maxArea;
};
```

---

## ⏱ Complexity

* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(1)`

✅ **Accepted** on LeetCode.

---

# 📊 Comparison

| Approach      | Time Complexity | Space Complexity | Status     |
| ------------- | ---------------- | ----------------- | ---------- |
| Brute Force   | `O(n²)`           | `O(1)`             | ❌ Too Slow |
| Two Pointers  | `O(n)`            | `O(1)`             | ✅ Optimal  |

---

# 📚 What You'll Learn

* Brute Force Thinking
* Two Pointer Technique
* Greedy Pointer Movement Intuition
* Pseudocode
* JavaScript Implementation
* Dry Run
* Time & Space Complexity
* Common Interview Mistakes

---

# 📖 Complete Explanation

This README is a quick overview.

For a **detailed explanation**, including:

* ✅ Intuition
* ✅ Visual diagrams
* ✅ Step-by-step dry run
* ✅ Why moving the shorter pointer works
* ✅ Common mistakes
* ✅ Interview tips

read the complete blog:

🔗 **https://ankitsingh2003.hashnode.dev/container-with-most-water-leetcode-11-from-brute-force-to-two-pointers-complete-beginner-guide**
