# Reverse Vowels of a String

## Solutions (JS)
Use two pointers to iterate over the string; one from the beginning, which appends consonants to a new result string; and one from the end, which is used to search for vowels to append to the result.

### Third, Final Submission
In this third submission, I used a `Set` declared inside the function to store the set of possible vowels.

In my testing, the cost of re-declaring the `Set` with every function call far outweighed the benefits of the optimized lookups. I believe my second submission would be fastest in real-world applications.

However, this is the one which LeetCode rated as the fastest and most memory efficient of my attempts.
```js
/**
 * @param {string} s
 * @return {string}
 */
function reverseVowels(s) {
  const vowels = new Set("aAeEiIoOuU");
  let result = "",
    j = s.length - 1;
  for (let i = 0; i < s.length; i++) {
    if (vowels.has(s[i])) {
      while (!vowels.has(s[j])) {
        j--;
      }
      result += s[j];
      j--;
    } else {
      result += s[i];
    }
  }
  return result;
}
```

### Second Submission
In my second submission, I opted to use a `Set` declared outside the function to store the set of possible vowels for lookup. This would mean the code takes advantage of the optimized lookups of `Set` while avoiding the cost of re-declaring a `Set` object every function call.

While this performed significantly faster than my first and third submissions in my testing for both chrome and firefox, LeetCode rated it as slower than both.
```js
const vowels = new Set("aAeEiIoOuU");

/**
 * @param {string} s
 * @return {string}
 */
function reverseVowels(s) {
  let result = "",
    j = s.length - 1;
  for (let i = 0; i < s.length; i++) {
    if (vowels.has(s[i])) {
      while (!vowels.has(s[j])) {
        j--;
      }
      result += s[j];
      j--;
    } else {
      result += s[i];
    }
  }
  return result;
}
```

### First Submission
In my first submission, the set of characters considered vowels is stored as a `string`; in my testing, this performed significantly faster in both chrome and firefox than re-declaring a `Set` of vowels every time the function is called.
```js
/**
 * @param {string} s
 * @return {string}
 */
function reverseVowels(s) {
  const vowels = "aAeEiIoOuU";
  let result = "",
    j = s.length - 1;
  for (let i = 0; i < s.length; i++) {
    if (vowels.includes(s[i])) {
      while (!vowels.includes(s[j])) {
        j--;
      }
      result += s[j];
      j--;
    } else {
      result += s[i];
    }
  }
  return result;
}
```
