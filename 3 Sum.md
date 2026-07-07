# LeetCode 15 – 3Sum

Given an integer array `nums`, return **all the unique triplets** `[nums[i], nums[j], nums[k]]` such that:

* `i != j`
* `i != k`
* `j != k`
* `nums[i] + nums[j] + nums[k] == 0`

The solution set **must not contain duplicate triplets**.

---

# 🟠 Brute Force Approach

## 💡 Idea

* Generate every possible triplet.
* Check whether the sum is `0`.
* Sort each valid triplet before storing it.
* Use a `Set` to remove duplicates.

---

## 📝 Pseudocode

```text
Create an empty Set
Create an empty answer array

For i from 0 to n-3
    For j from i+1 to n-2
        For k from j+1 to n-1

            If nums[i] + nums[j] + nums[k] == 0

                Create triplet
                Sort triplet

                Convert triplet to string

                If string not present in Set
                    Add to Set
                    Push triplet into answer

Return answer
```

---

## 💻 JavaScript

```javascript
var threeSum = function(nums) {
    const set = new Set();
    const ans = [];
    const n = nums.length;

    for (let i = 0; i < n - 2; i++) {
        for (let j = i + 1; j < n - 1; j++) {
            for (let k = j + 1; k < n; k++) {

                if (nums[i] + nums[j] + nums[k] === 0) {

                    const triplet = [nums[i], nums[j], nums[k]].sort((a, b) => a - b);
                    const key = triplet.join(",");

                    if (!set.has(key)) {
                        set.add(key);
                        ans.push(triplet);
                    }
                }
            }
        }
    }

    return ans;
};
```

---

## ⏱ Complexity

* **Time Complexity:** `O(n³)`
* **Space Complexity:** `O(k)` *(for storing unique triplets)*

> **Note:** Although easy to understand, this approach becomes very slow for large inputs.

---

# 🟢 Optimal Approach (Sorting + Two Pointers)

## 💡 Idea

* Sort the array.
* Fix one element.
* Use two pointers to find the remaining two numbers.
* Skip duplicate values to avoid duplicate triplets.

---

## 📝 Pseudocode

```text
Sort the array

For every index i

    If current value is duplicate
        Continue

    left = i + 1
    right = n - 1

    While left < right

        sum = nums[i] + nums[left] + nums[right]

        If sum < 0
            Move left

        Else if sum > 0
            Move right

        Else

            Store triplet

            Move left forward
            Move right backward

            Skip duplicate values of left
            Skip duplicate values of right

Return answer
```

---

## 💻 JavaScript

```javascript
var threeSum = function(nums) {

    nums.sort((a, b) => a - b);

    const ans = [];
    const n = nums.length;

    for (let i = 0; i < n - 2; i++) {

        if (i > 0 && nums[i] === nums[i - 1]) {
            continue;
        }

        let left = i + 1;
        let right = n - 1;

        while (left < right) {

            const sum = nums[i] + nums[left] + nums[right];

            if (sum < 0) {
                left++;
            } else if (sum > 0) {
                right--;
            } else {

                ans.push([nums[i], nums[left], nums[right]]);

                left++;
                right--;

                while (left < right && nums[left] === nums[left - 1]) {
                    left++;
                }

                while (left < right && nums[right] === nums[right + 1]) {
                    right--;
                }
            }
        }
    }

    return ans;
};
```

---

## ⏱ Complexity

* **Time Complexity:** `O(n²)`
* **Space Complexity:** `O(1)` *(excluding the output array)*

✅ **Accepted** on LeetCode.

---

# 📊 Comparison

| Approach               | Time Complexity | Space Complexity            | Status     |
| ---------------------- | --------------- | --------------------------- | ---------- |
| Brute Force            | `O(n³)`         | `O(k)`                      | ❌ Too Slow |
| Sorting + Two Pointers | `O(n²)`         | `O(1)` *(excluding output)* | ✅ Optimal  |

---

# 📚 What You'll Learn

* Brute Force Thinking
* Two Pointer Technique
* Sorting
* Duplicate Handling
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
* ✅ Duplicate handling explained
* ✅ Common mistakes
* ✅ Interview tips

read the complete blog:

🔗 **https://ankitsingh2003.hashnode.dev/mastering-leetcode-15-3sum**
