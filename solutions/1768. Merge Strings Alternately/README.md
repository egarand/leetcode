# Merge Strings Alternately

You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return _the merged string._

## Solution (JS)
Use one pointer to iterate over both input strings, adding a character from both inputs each loop until there are no more characters in either string.
```js
/**
 * @param {string} word1
 * @param {string} word2
 * @return {string}
 */
function mergeAlternately(word1, word2) {
  const maxLen = Math.max(word1.length, word2.length);
  let result = "";
  for (let i = 0; i < maxLen; i++) {
    if (i < word1.length) {
      result += word1[i];
    }
    if (i < word2.length) {
      result += word2[i];
    }
  }
  return result;
}
```
