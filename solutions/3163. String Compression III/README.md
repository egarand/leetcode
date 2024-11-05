# String Compression III

Given a string `word`, compress it using the following algorithm:

- Begin with an empty string `comp`. While `word` is **not** empty, use the following operation:
    - Remove a maximum length prefix of `word` made of a _single character_ `c` repeating **at most** 9 times.
    - Append the length of the prefix followed by `c` to `comp`.

Return the string `comp`.

## Solutions (JS)

### Submitted
Iterate over the string, counting sequences of repeating characters and adding them to the result as we go.
```js
/**
 * @param {string} word
 * @return {string}
 */
function compressedString(word) {
  let comp = "";
  for (let i = 0; i < word.length;) {
    let char = word[i],
      count = 0,
      limit = Math.min(word.length, i + 9);
    while (i < limit && word[i] === char) {
      count++;
      i++;
    }
    comp += count + char;
  }
  return comp;
}
```

### Other
Use a regular expression to match sequences of 9 or fewer repeated characters, and append the length and subject of each match to the result.

Not submitted due to regex's slow performance.
```js
/**
 * @param {string} word
 * @return {string}
 */
function compressedString(word) {
  const regex = /([a-z])\1{0,8}/g;
  let comp = "", match;
  while ((match = regex.exec(word)) !== null) {
    comp += match[0].length + match[1];
  }
  return comp;
}
```
