# Leetcode_Day85
# Day 85: Majority Element II

**LeetCode Problem:** 229. Majority Element II  
**Difficulty:** Medium  
**Language:** Java  
**Topic:** Arrays, HashMap, Frequency Counting

## Problem Statement

Given an integer array `nums` of size `n`, find all elements that appear more than `n / 3` times.

Return the elements in any order.

## Approach: HashMap

I solved this problem using a `HashMap` to count the frequency of each element.

### Steps

1. Create a `HashMap` to store each element and its frequency.
2. Traverse the array and update the frequency of every element using `getOrDefault()`.
3. Create an `ArrayList` to store the majority elements.
4. Traverse the map and check whether each element appears more than `n / 3` times.
5. Add the elements satisfying this condition to the result list.
6. Return the list.

## Java Solution

```java
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();

        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        ArrayList<Integer> list = new ArrayList<>();

        for (int key : map.keySet()) {
            if (map.get(key) > nums.length / 3) {
                list.add(key);
            }
        }

        return list;
    }
}
```

## Example

**Input:**
```text
nums = [3, 2, 3]
```

**Output:**
```text
[3]
```

**Explanation:**

The array has 3 elements, so the threshold is `3 / 3 = 1`.

The element `3` appears twice, which is more than 1. Therefore, the answer is `[3]`.

## Complexity Analysis

- **Time Complexity:** O(n), on average, to count the frequencies and examine the map.
- **Space Complexity:** O(n), because the HashMap can store up to n distinct elements.

## What I Learned

- How to use a HashMap to count element frequencies.
- How `getOrDefault()` simplifies frequency counting in Java.
- How to apply a condition based on the array's length.
- Why the condition must be strictly greater than `n / 3`, not greater than or equal to it.

## Key Observation

There can be **at most two elements** that appear more than `n / 3` times in an array.

This is because three different elements appearing more than one-third of the array each would require more elements than the array contains.

## Takeaway

This problem reminded me that understanding the condition carefully is just as important as writing the code. Sometimes, a simple frequency-counting approach is a great way to build a strong foundation before exploring more optimized algorithms.
