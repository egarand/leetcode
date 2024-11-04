# Palindrome Number

Given an integer `x`, return `true` if `x` is a _**palindrome**_, and `false` otherwise.

**Follow up:** Could you solve it without converting the integer to a string?

## Solution (JS)
Without converting the integer to a string, use a loop to repeatedly compare the first and last digits of the number and then remove those digits from the number.
```js
/**
 * @param {number} x
 * @return {boolean}
 */
function isPalindrome(x) {
  if (x < 0) {
    return false;
  }
  const digits = Math.floor(Math.log10(x)) + 1;
  let divisor = Math.pow(10, digits - 1);
  while (x !== 0) {
    const firstDigit = Math.floor(x / divisor),
      lastDigit = x % 10;
    if (firstDigit !== lastDigit) {
      return false;
    }
    x = Math.floor((x % divisor) / 10);
    divisor /= 100;
  }
  return true;
};
```