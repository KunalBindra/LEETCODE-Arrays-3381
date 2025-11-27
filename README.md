# LEETCODE-Arrays-3381
```
nums = [-1, -2, 3, 4, -5]
k = 2
```

---

# ✅ **Step 1: Compute Prefix Sum**

`prefix[i] = sum of nums[0..i]`

| i | nums[i] | prefix[i] |
| - | ------- | --------- |
| 0 | -1      | -1        |
| 1 | -2      | -3        |
| 2 | 3       | 0         |
| 3 | 4       | 4         |
| 4 | -5      | -1        |

So:
`prefix = [-1, -3, 0, 4, -1]`

---

# ✅ **Step 2: Main Logic**

Outer loop: `start = 0` and `start = 1` (because `start < k`)

---

# ⭐ **Case 1: start = 0**

```
currsum = 0
i = 0
```

## Iteration 1:

* `i = 0`
* `j = i + k - 1 = 0 + 2 - 1 = 1`
* subarray = nums[0..1] = [-1, -2]
* `subsum = prefix[1] - prefix[-1] = -3`

```
currsum = max(-3, 0 + -3) = -3
result  = max(-∞, -3) = -3
```

`i = i + k = 2`

---

## Iteration 2:

* `i = 2`
* `j = 2 + 2 - 1 = 3`
* subarray = nums[2..3] = [3, 4]
* `subsum = prefix[3] - prefix[1] = 4 - (-3) = 7`

```
currsum = max(7, -3 + 7) = 7
result  = max(-3, 7) = 7
```

`i = i + k = 4`

---

## Iteration 3:

* `i = 4`
* `j = 4 + 2 - 1 = 5` → **out of bounds**, stop.

---

### ✔ End of start=0

`result = 7`

---

# ⭐ **Case 2: start = 1**

```
currsum = 0
i = 1
```

## Iteration 1:

* `i = 1`
* `j = 1 + 2 - 1 = 2`
* subarray = nums[1..2] = [-2, 3]
* `subsum = prefix[2] - prefix[0] = 0 - (-1) = 1`

```
currsum = max(1, 0 + 1) = 1
result  = max(7, 1) = 7
```

`i = 3`

---

## Iteration 2:

* `i = 3`
* `j = 3 + 2 - 1 = 4`
* subarray = nums[3..4] = [4, -5]
* `subsum = prefix[4] - prefix[2] = -1 - 0 = -1`

```
currsum = max(-1, 1 + -1) = 0
result  = max(7, 0) = 7
```

`i = 5` → stop.

---

### ✔ End of start=1

`result = 7`

---

# 🎉 **FINAL ANSWER**

```
result = 7
```

# 📌 **Which subarray gave this?**

At `start = 0`, `i = 2`:

Subarray = `[3, 4]` → sum = **7**

---

If you want, I can also rewrite or optimize the code.
