# Valid Palindrome

**Problem:** Given a string `s`, return `true` if it is a palindrome after converting all uppercase letters into lowercase and removing all non-alphanumeric characters. Otherwise, return `false`.

---

## 🟠 Brute Force Approach

### Idea

- Convert the string to lowercase.
- Remove all non-alphanumeric characters.
- Reverse the cleaned string.
- Compare the original cleaned string with the reversed string.
- If both are equal, it is a palindrome.

### Code

```javascript
var isPalindrome = function(s) {
    s = s.toLowerCase().replace(/[^a-z0-9]/g, "");

    let rev = "";

    for (let i = s.length - 1; i >= 0; i--) {
        rev += s[i];
    }

    return s === rev;
};
```

### Complexity

- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(n)`

> **Note:** This approach is simple and easy to understand but requires extra space to create the reversed string.

---

## 🟢 Optimal Approach (Two Pointers)

### Idea

Instead of creating a new string:

- Start one pointer from the beginning.
- Start another pointer from the end.
- Skip characters that are **not letters or digits**.
- Compare characters ignoring case.
- If they don't match, return `false`.
- Continue until both pointers meet.

### Code

```javascript
var isPalindrome = function(s) {
    let left = 0;
    let right = s.length - 1;

    while (left < right) {

        while (left < right && !/[a-z0-9]/i.test(s[left])) {
            left++;
        }

        while (left < right && !/[a-z0-9]/i.test(s[right])) {
            right--;
        }

        if (s[left].toLowerCase() !== s[right].toLowerCase()) {
            return false;
        }

        left++;
        right--;
    }

    return true;
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
| Brute Force (Reverse String) | `O(n)` | `O(n)` | ✅ Accepted |
| Two Pointers | `O(n)` | `O(1)` | ✅ Optimal & Accepted |

---

## Why Two Pointers?

The array/string doesn't need to be modified or copied.

- ✅ Avoids creating a reversed string.
- ✅ Uses constant extra memory.
- ✅ Efficiently skips spaces, punctuation, and special characters.
- ✅ Compares characters from both ends in a single traversal.

This makes the **Two Pointer** approach the preferred solution for the **Valid Palindrome** problem.
