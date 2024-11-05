# Kids With the Greatest Number of Candies

There are `n` kids with candies. You are given an integer array `candies`, where each `candies[i]` represents the number of candies the i<sup>th</sup> kid has, and an integer `extraCandies`, denoting the number of extra candies that you have.

Return _a boolean array `result` of length `n`, where `result[i]` is `true` if, after giving the i<sup>th</sup> kid all the `extraCandies`, they will have the **greatest** number of candies among all the kids, or `false` otherwise._

Note that **multiple** kids can have the **greatest** number of candies.

## Solution (JS)
First, find the maximum number of candies held by any kid in the array; this is done by sorting the array and taking the last element. Then, check if each kid's candy amount plus the extras would match or exceed the found maximum.
```js
/**
 * @param {number[]} candies
 * @param {number} extraCandies
 * @return {boolean[]}
 */
function kidsWithCandies(candies, extraCandies) {
  const maxCandies = candies.toSorted((a, b) => a - b).at(-1);
  return candies.map((k) => k + extraCandies >= maxCandies);
}
```
