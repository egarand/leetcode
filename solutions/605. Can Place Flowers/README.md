# Can Place Flowers

You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in **adjacent** plots.

Given an integer array `flowerbed` containing `0`'s and `1`'s, where `0` means empty and `1` means not empty, and an integer `n`, return `true` _if `n` new flowers can be planted in the `flowerbed` without violating the no-adjacent-flowers rule and `false` otherwise._

## Solution (JS)
Iterate through the flowerbed, counting pots which are available by decrementing `n`, and returning `true` as soon as we've found enough free pots; if `n` never reaches 0, return `false`.
```js
/**
 * @param {number[]} flowerbed
 * @param {number} n
 * @return {boolean}
 */
function canPlaceFlowers(flowerbed, n) {
  if (n === 0) {
    return true;
  }
  for (let i = 0; i < flowerbed.length; i++) {
    if (
      flowerbed[i] === 0
      && (i === 0 || flowerbed[i-1] === 0)
      && (i === flowerbed.length - 1 || flowerbed[i+1] === 0)
    ) {
      n--;
      i++;
      if (n <= 0) {
        return true;
      }
    }
  }
  return false;
}
```