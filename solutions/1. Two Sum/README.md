# Two Sum

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Follow-up:** Can you come up with an algorithm that is less than O(n<sup>2</sup>) time complexity?

## Solution (JS)
Iterate over the array, keeping a map of each number and its index as we go, until we find a number with a complement in the map that adds up to the target.
- Time Complexity: O(n)
- Space Complexity: O(n)
```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
function twoSum(nums, target) {
  const complements = new Map();

  for (let i = 0; i < nums.length; i++) {
    let complement = target - nums[i];
    if (complements.has(complement)) {
      return [complements.get(complement), i];
    } else {
      complements.set(nums[i], i);
    }
  }
};
```