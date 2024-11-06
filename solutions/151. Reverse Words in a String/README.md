# Reverse Words in a String

Given an input string `s`, reverse the order of the **words**.

A **word** is defined as a sequence of non-space characters. The **words** in `s` will be separated by at least one space.

Return _a string of the words in reverse order concatenated by a single space._

**Note** that `s` may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

## Solution (JS)
Split the string into an array of words. Then, iterate over the array in reverse, skipping empty items that come from multiple consecutive spaces, and concatenate each word to an output string.
```js
/**
 * @param {string} s
 * @return {string}
 */
function reverseWords(s) {
  const words = s.split(" ");
  let result = "";
  for (let i = words.length - 1; i >= 0; i--) {
    if (words[i]) {
      result += words[i];
    }
    if (result && words[i-1]) {
      result += " ";
    }
  }
  return result;
}
```
