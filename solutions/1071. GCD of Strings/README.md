# Greatest Common Divisor of Strings

For two strings `s` and `t`, we say "`t` divides `s`" if and only if `s = t + t + t + ... + t + t` (i.e., `t` is concatenated with itself one or more times).

Given two strings `str1` and `str2`, return the largest string `x` such that `x` divides both `str1` and `str2`.

## Solutions (JS)

### Final Submission
First, check if the strings contain only the same repeating pattern by checking their equality when concatenated in different orders. Then, find the GCD of their lengths using the Euclidean algorithm; a prefix of one of the strings of that length is the GCD of the two strings.
```js
/**
 * Euclidean algorithm for finding the GCD of two numbers.
 * @param {number} a
 * @param {number} b
 * @return {number}
 */
function gcd(a, b) {
  while (b) {
    [a, b] = [b, a % b];
  }
  return a;
}

/**
 * @param {string} str1
 * @param {string} str2
 * @return {string}
 */
function gcdOfStrings(str1, str2) {
  if (str1 + str2 !== str2 + str1) {
    return "";
  }
  return str1.substring(0, gcd(str1.length, str2.length));
}
```

### First Submission
First, find the GCD of the length of the strings using the Euclidean algorithm. Then, take a prefix of either string of that length; this is the GCD of the strings. Finally, use a regular expression to test if both strings consist only of that divisor repeated 0+ times.

The regular expression seemed more intuitive to me, and performed better than the final submission in the limited testing I did in firefox; but ultimately, cutting out regex and testing if finding a GCD is possible _before_ running the calculation for the GCD's length is faster.
```js
/**
 * Euclidean algorithm for finding the GCD of two numbers.
 * @param {number} a
 * @param {number} b
 * @return {number}
 */
function gcd(a, b) {
  while (b) {
    [a, b] = [b, a % b];
  }
  return a;
}

/**
 * @param {string} str1
 * @param {string} str2
 * @return {string}
 */
function gcdOfStrings(str1, str2) {
  const divisor = str1.substring(0, gcd(str1.length, str2.length));
  const regex = new RegExp(`^(?:${divisor})*$`);
  if (regex.test(str1) && regex.test(str2)) {
    return divisor;
  }
  return "";
}